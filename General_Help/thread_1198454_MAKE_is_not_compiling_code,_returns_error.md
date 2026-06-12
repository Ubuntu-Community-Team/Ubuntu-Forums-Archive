---
title: "MAKE is not compiling code, returns error"
date: 2009-06-27
forum: General Help
---

### Post by WarholsGhost on 2009-06-27
I'm trying to compile keepassX for a project and it doesn't want to compile, i'v been having the problem with make with a few other files too here is the output:

```

cd src && make -f Makefile
make[1]: Entering directory `/home/frenzy/Desktop/keepassx-0.4.0/src'
Makefile:1034: warning: overriding commands for target `../build/AutoTypeDlg.o'
Makefile:579: warning: ignoring old commands for target `../build/AutoTypeDlg.o'
Makefile:1040: warning: overriding commands for target `../build/TargetWindowDlg.o'
Makefile:589: warning: ignoring old commands for target `../build/TargetWindowDlg.o'
Makefile:1045: warning: overriding commands for target `../build/AboutDlg.o'
Makefile:780: warning: ignoring old commands for target `../build/AboutDlg.o'
Makefile:1050: warning: overriding commands for target `../build/AddBookmarkDlg.o'
Makefile:785: warning: ignoring old commands for target `../build/AddBookmarkDlg.o'
Makefile:1055: warning: overriding commands for target `../build/CalendarDlg.o'
Makefile:790: warning: ignoring old commands for target `../build/CalendarDlg.o'
Makefile:1060: warning: overriding commands for target `../build/CollectEntropyDlg.o'
Makefile:795: warning: ignoring old commands for target `../build/CollectEntropyDlg.o'
Makefile:1065: warning: overriding commands for target `../build/CustomizeDetailViewDlg.o'
Makefile:800: warning: ignoring old commands for target `../build/CustomizeDetailViewDlg.o'
Makefile:1071: warning: overriding commands for target `../build/DatabaseSettingsDlg.o'
Makefile:806: warning: ignoring old commands for target `../build/DatabaseSettingsDlg.o'
Makefile:1081: warning: overriding commands for target `../build/EditEntryDlg.o'
Makefile:816: warning: ignoring old commands for target `../build/EditEntryDlg.o'
Makefile:1087: warning: overriding commands for target `../build/EditGroupDlg.o'
Makefile:822: warning: ignoring old commands for target `../build/EditGroupDlg.o'
Makefile:1092: warning: overriding commands for target `../build/ExpiredEntriesDlg.o'
Makefile:827: warning: ignoring old commands for target `../build/ExpiredEntriesDlg.o'
Makefile:1102: warning: overriding commands for target `../build/ManageBookmarksDlg.o'
Makefile:833: warning: ignoring old commands for target `../build/ManageBookmarksDlg.o'
Makefile:1107: warning: overriding commands for target `../build/PasswordDlg.o'
Makefile:838: warning: ignoring old commands for target `../build/PasswordDlg.o'
Makefile:1119: warning: overriding commands for target `../build/PasswordGenDlg.o'
Makefile:850: warning: ignoring old commands for target `../build/PasswordGenDlg.o'
Makefile:1124: warning: overriding commands for target `../build/SearchDlg.o'
Makefile:855: warning: ignoring old commands for target `../build/SearchDlg.o'
Makefile:1129: warning: overriding commands for target `../build/SelectIconDlg.o'
Makefile:860: warning: ignoring old commands for target `../build/SelectIconDlg.o'
Makefile:1136: warning: overriding commands for target `../build/SettingsDlg.o'
Makefile:867: warning: ignoring old commands for target `../build/SettingsDlg.o'
Makefile:1141: warning: overriding commands for target `../build/SimplePasswordDlg.o'
Makefile:872: warning: ignoring old commands for target `../build/SimplePasswordDlg.o'
Makefile:1267: warning: overriding commands for target `../build/moc_AutoTypeDlg.o'
Makefile:1151: warning: ignoring old commands for target `../build/moc_AutoTypeDlg.o'
Makefile:1270: warning: overriding commands for target `../build/moc_TargetWindowDlg.o'
Makefile:1157: warning: ignoring old commands for target `../build/moc_TargetWindowDlg.o'
Makefile:1273: warning: overriding commands for target `../build/moc_AboutDlg.o'
Makefile:1197: warning: ignoring old commands for target `../build/moc_AboutDlg.o'
Makefile:1276: warning: overriding commands for target `../build/moc_AddBookmarkDlg.o'
Makefile:1200: warning: ignoring old commands for target `../build/moc_AddBookmarkDlg.o'
Makefile:1279: warning: overriding commands for target `../build/moc_CalendarDlg.o'
Makefile:1203: warning: ignoring old commands for target `../build/moc_CalendarDlg.o'
Makefile:1282: warning: overriding commands for target `../build/moc_CollectEntropyDlg.o'
Makefile:1206: warning: ignoring old commands for target `../build/moc_CollectEntropyDlg.o'
Makefile:1285: warning: overriding commands for target `../build/moc_CustomizeDetailViewDlg.o'
Makefile:1209: warning: ignoring old commands for target `../build/moc_CustomizeDetailViewDlg.o'
Makefile:1288: warning: overriding commands for target `../build/moc_DatabaseSettingsDlg.o'
Makefile:1212: warning: ignoring old commands for target `../build/moc_DatabaseSettingsDlg.o'
Makefile:1291: warning: overriding commands for target `../build/moc_EditEntryDlg.o'
Makefile:1215: warning: ignoring old commands for target `../build/moc_EditEntryDlg.o'
Makefile:1294: warning: overriding commands for target `../build/moc_EditGroupDlg.o'
Makefile:1218: warning: ignoring old commands for target `../build/moc_EditGroupDlg.o'
Makefile:1297: warning: overriding commands for target `../build/moc_ExpiredEntriesDlg.o'
Makefile:1221: warning: ignoring old commands for target `../build/moc_ExpiredEntriesDlg.o'
Makefile:1303: warning: overriding commands for target `../build/moc_ManageBookmarksDlg.o'
Makefile:1224: warning: ignoring old commands for target `../build/moc_ManageBookmarksDlg.o'
Makefile:1306: warning: overriding commands for target `../build/moc_PasswordDlg.o'
Makefile:1227: warning: ignoring old commands for target `../build/moc_PasswordDlg.o'
Makefile:1310: warning: overriding commands for target `../build/moc_PasswordGenDlg.o'
Makefile:1231: warning: ignoring old commands for target `../build/moc_PasswordGenDlg.o'
Makefile:1313: warning: overriding commands for target `../build/moc_SearchDlg.o'
Makefile:1234: warning: ignoring old commands for target `../build/moc_SearchDlg.o'
Makefile:1316: warning: overriding commands for target `../build/moc_SelectIconDlg.o'
Makefile:1237: warning: ignoring old commands for target `../build/moc_SelectIconDlg.o'
Makefile:1319: warning: overriding commands for target `../build/moc_SettingsDlg.o'
Makefile:1240: warning: ignoring old commands for target `../build/moc_SettingsDlg.o'
Makefile:1322: warning: overriding commands for target `../build/moc_SimplePasswordDlg.o'
Makefile:1243: warning: ignoring old commands for target `../build/moc_SimplePasswordDlg.o'
Makefile:1439: warning: overriding commands for target `../build/moc/moc_AutoTypeDlg.cpp'
Makefile:1331: warning: ignoring old commands for target `../build/moc/moc_AutoTypeDlg.cpp'
Makefile:1442: warning: overriding commands for target `../build/moc/moc_TargetWindowDlg.cpp'
Makefile:1337: warning: ignoring old commands for target `../build/moc/moc_TargetWindowDlg.cpp'
Makefile:1445: warning: overriding commands for target `../build/moc/moc_AboutDlg.cpp'
Makefile:1370: warning: ignoring old commands for target `../build/moc/moc_AboutDlg.cpp'
Makefile:1448: warning: overriding commands for target `../build/moc/moc_AddBookmarkDlg.cpp'
Makefile:1373: warning: ignoring old commands for target `../build/moc/moc_AddBookmarkDlg.cpp'
Makefile:1451: warning: overriding commands for target `../build/moc/moc_CalendarDlg.cpp'
Makefile:1376: warning: ignoring old commands for target `../build/moc/moc_CalendarDlg.cpp'
Makefile:1454: warning: overriding commands for target `../build/moc/moc_CollectEntropyDlg.cpp'
Makefile:1379: warning: ignoring old commands for target `../build/moc/moc_CollectEntropyDlg.cpp'
Makefile:1457: warning: overriding commands for target `../build/moc/moc_CustomizeDetailViewDlg.cpp'
Makefile:1382: warning: ignoring old commands for target `../build/moc/moc_CustomizeDetailViewDlg.cpp'
Makefile:1460: warning: overriding commands for target `../build/moc/moc_DatabaseSettingsDlg.cpp'
Makefile:1385: warning: ignoring old commands for target `../build/moc/moc_DatabaseSettingsDlg.cpp'
Makefile:1463: warning: overriding commands for target `../build/moc/moc_EditEntryDlg.cpp'
Makefile:1388: warning: ignoring old commands for target `../build/moc/moc_EditEntryDlg.cpp'
Makefile:1466: warning: overriding commands for target `../build/moc/moc_EditGroupDlg.cpp'
Makefile:1391: warning: ignoring old commands for target `../build/moc/moc_EditGroupDlg.cpp'
Makefile:1469: warning: overriding commands for target `../build/moc/moc_ExpiredEntriesDlg.cpp'
Makefile:1394: warning: ignoring old commands for target `../build/moc/moc_ExpiredEntriesDlg.cpp'
Makefile:1475: warning: overriding commands for target `../build/moc/moc_ManageBookmarksDlg.cpp'
Makefile:1397: warning: ignoring old commands for target `../build/moc/moc_ManageBookmarksDlg.cpp'
Makefile:1478: warning: overriding commands for target `../build/moc/moc_PasswordDlg.cpp'
Makefile:1400: warning: ignoring old commands for target `../build/moc/moc_PasswordDlg.cpp'
Makefile:1481: warning: overriding commands for target `../build/moc/moc_PasswordGenDlg.cpp'
Makefile:1403: warning: ignoring old commands for target `../build/moc/moc_PasswordGenDlg.cpp'
Makefile:1484: warning: overriding commands for target `../build/moc/moc_SearchDlg.cpp'
Makefile:1406: warning: ignoring old commands for target `../build/moc/moc_SearchDlg.cpp'
Makefile:1487: warning: overriding commands for target `../build/moc/moc_SelectIconDlg.cpp'
Makefile:1409: warning: ignoring old commands for target `../build/moc/moc_SelectIconDlg.cpp'
Makefile:1490: warning: overriding commands for target `../build/moc/moc_SettingsDlg.cpp'
Makefile:1412: warning: ignoring old commands for target `../build/moc/moc_SettingsDlg.cpp'
Makefile:1493: warning: overriding commands for target `../build/moc/moc_SimplePasswordDlg.cpp'
Makefile:1415: warning: ignoring old commands for target `../build/moc/moc_SimplePasswordDlg.cpp'
/usr/share/qt3/bin/uic forms/AboutDlg.ui -o ../build/ui/AboutDlg.h
uic: File generated with too recent version of Qt Designer (4.0 vs. 3.3.8b)
make[1]: *** [../build/ui/AboutDlg.h] Error 1
make[1]: Leaving directory `/home/frenzy/Desktop/keepassx-0.4.0/src'
make: *** [sub-src] Error 2

```

anything helps

---

### Post by mc4man on 2009-06-27
I'd think more like cd to your extracted source (..../keepassx-0.4.0$) and run 
qmake-qt4
make
sudo make install

you may prefer to just install as a deb package (available for 7.10 thru 9.04

[https://launchpad.net/~keepassx/+archive/ppa](https://launchpad.net/~keepassx/+archive/ppa)

---

### Post by WarholsGhost on 2009-06-28
thats what i did to get that error, i need the code to become an executable to go on a USB drive.

---

### Post by mc4man on 2009-06-28
> thats what i did to get that error
2 things
What you've posted is cd'ing to src,...why?
Maybe I'm not understanding what you want

> doug@doug-laptop:~/Desktop/[COLOR="Blue"]keepassx-0.4.0$[/COLOR] qmake-qt4
Project MESSAGE: See 'INSTALL' for configuration options.
Project MESSAGE: Install Prefix: /usr
Project MESSAGE: *** Makefile successfully generated.
Project MESSAGE: *** Start make now.
doug@doug-laptop:~/Desktop/[COLOR="Blue"]keepassx-0.4.0$[/COLOR] make
.............succeeds  

an exec will be found in keepassx-0.4.0/bin and runs as standalone (no 'sudo make install' used
> doug@doug-laptop:~/Desktop/keepassx-0.4.0/bin$ ./keepassx

---

### Post by flugh on 2009-06-28
```

/usr/share/qt3/bin/uic forms/AboutDlg.ui -o ../build/ui/AboutDlg.h
uic: File generated with too recent version of Qt Designer (4.0 vs. 3.3.8b)

```
I would look at your Qt Designer version? Usually doing ./configure --help (or maybe --options) will give a list of command line options you can feed to configure. Maybe there's one to ignore the Qt Designer version. Maybe consider installing the version this source code calls for (3.3.8b), or possibly the version you have installed can update/migrate it somehow (just a --reconfigure sort of option).

That's all pseudo-thought there, as I have zero experience with those particular programs.

---

