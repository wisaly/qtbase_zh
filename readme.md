qtbase_zh_CN.ts

不知什么原因，官方发布的Qt5.2不包含qtbase系列的中文翻译。
这将导致QMessageBox的按钮无法汉化，因为它最终调用了QPlatformTheme的相关函数，而QPlatformTheme不包含在qt_zh_CN中。

所有和qt_zh_CN.ts重复的文本都已经翻译（使用TsSync工具），剩下的翻译了一部分，有精力的人可以尝试都翻译完。

usage:
```
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);

    QTranslator qtTranslator;
    qtTranslator.load("qt_zh_CN.qm", QLibraryInfo::location(QLibraryInfo::TranslationsPath));
    app.installTranslator(&qtTranslator);

    QTranslator qtbaseTranslator;
    qtbaseTranslator.load("qtbase_zh.qm");
    app.installTranslator(&qtbaseTranslator);

    ...
    return app.exec();
}
```
