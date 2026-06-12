---
title: "Problem with compiling (front-end for aircrack)"
date: 2009-07-19
forum: General Help
---

### Post by hotshot247 on 2009-07-19
i'm trying to compile qaircrack-ng which is the front-end of aircrack and i installed the plugins that it wanted me to and then when i tried to compile it, it says "warning: ‘sorcerynet’ defined but not used" and i have no idea what to do now. any help would be appreciated. thanks in advance!

---

### Post by michy99 on 2009-07-19
As long as it is a warning and not an error, it should still compile and run.

---

### Post by hotshot247 on 2009-07-19
it had a bunch more stuff as well. some of which had errors. i'll just copy and paste everything. 

g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o MainWindow.o MainWindow.cpp
In file included from MainWindow.cpp:15:
MainWindow.h:18:27: error: QApplication: No such file or directory
MainWindow.h:19:26: error: QMainWindow: No such file or directory
MainWindow.h:20:26: error: QHBoxLayout: No such file or directory
MainWindow.h:21:26: error: QVBoxLayout: No such file or directory
MainWindow.h:22:25: error: QTabWidget: No such file or directory
MainWindow.h:23:26: error: QMessageBox: No such file or directory
MainWindow.h:24:20: error: QIcon: No such file or directory
MainWindow.h:25:22: error: QPixmap: No such file or directory
In file included from MainWindow.h:27,
                 from MainWindow.cpp:15:
ACcommon.h:19:22: error: QString: No such file or directory
ACcommon.h:21:22: error: QWidget: No such file or directory
ACcommon.h:24:24: error: QComboBox: No such file or directory
ACcommon.h:25:21: error: QLabel: No such file or directory
ACcommon.h:26:24: error: QTextLine: No such file or directory
ACcommon.h:27:27: error: QTableWidget: No such file or directory
ACcommon.h:28:31: error: QTableWidgetItem: No such file or directory
ACcommon.h:29:26: error: QPushButton: No such file or directory
ACcommon.h:30:23: error: QProcess: No such file or directory
ACcommon.h:31:26: error: QStringList: No such file or directory
ACcommon.h:32:24: error: QCheckBox: No such file or directory
In file included from MainWindow.h:28,
                 from MainWindow.cpp:15:
ACscan.h:36:42: error: voodoo2/datastructure/csv.h: No such file or directory
In file included from MainWindow.h:29,
                 from MainWindow.cpp:15:
ACcapture.h:21:24: error: QGroupBox: No such file or directory
ACcapture.h:26:23: error: QWebView: No such file or directory
ACcapture.h:27:28: error: QTextDocument: No such file or directory
ACcapture.h:28:23: error: QSpinBox: No such file or directory
In file included from MainWindow.h:31,
                 from MainWindow.cpp:15:
ACcrack.h:30:26: error: QFileDialog: No such file or directory
In file included from MainWindow.h:27,
                 from MainWindow.cpp:15:
ACcommon.h:42: error: ‘QString’ does not name a type
ACcommon.h:43: error: ‘QString’ does not name a type
ACcommon.h:44: error: ‘QString’ does not name a type
ACcommon.h:45: error: ‘QString’ does not name a type
ACcommon.h:46: error: ‘QString’ does not name a type
ACcommon.h:48: error: ‘QString’ has not been declared
ACcommon.h:49: error: ‘QString’ has not been declared
ACcommon.h:50: error: ‘QString’ has not been declared
ACcommon.h:51: error: ‘QString’ has not been declared
ACcommon.h:52: error: ‘QString’ has not been declared
ACcommon.h:54: error: ‘QString’ does not name a type
ACcommon.h:55: error: ‘QString’ does not name a type
ACcommon.h:56: error: ‘QString’ does not name a type
ACcommon.h:57: error: ‘QString’ does not name a type
ACcommon.h:58: error: ‘QString’ does not name a type
In file included from MainWindow.h:28,
                 from MainWindow.cpp:15:
ACscan.h:44: error: expected class-name before ‘{’ token
ACscan.h:45: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
ACscan.h:47: error: expected ‘;’ before ‘private’
ACscan.h:50: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACscan.h:50: error: expected ‘;’ before ‘*’ token
ACscan.h:51: error: ISO C++ forbids declaration of ‘QHBoxLayout’ with no type
ACscan.h:51: error: expected ‘;’ before ‘*’ token
ACscan.h:53: error: ISO C++ forbids declaration of ‘QLabel’ with no type
ACscan.h:53: error: expected ‘;’ before ‘*’ token
ACscan.h:54: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACscan.h:54: error: expected ‘;’ before ‘*’ token
ACscan.h:55: error: ISO C++ forbids declaration of ‘QPushButton’ with no type
ACscan.h:55: error: expected ‘;’ before ‘*’ token
ACscan.h:57: error: ISO C++ forbids declaration of ‘QCheckBox’ with no type
ACscan.h:57: error: expected ‘;’ before ‘*’ token
ACscan.h:59: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACscan.h:59: error: expected ‘;’ before ‘*’ token
ACscan.h:62: error: ISO C++ forbids declaration of ‘QTableWidget’ with no type
ACscan.h:62: error: expected ‘;’ before ‘*’ token
ACscan.h:63: error: ISO C++ forbids declaration of ‘CSV’ with no type
ACscan.h:63: error: expected ‘;’ before ‘*’ token
ACscan.h:65: error: ISO C++ forbids declaration of ‘QPushButton’ with no type
ACscan.h:65: error: expected ‘;’ before ‘*’ token
ACscan.h:72: error: expected `:' before ‘slots’
ACscan.h:73: error: expected primary-expression before ‘void’
ACscan.h:73: error: ISO C++ forbids declaration of ‘slots’ with no type
ACscan.h:73: error: expected ‘;’ before ‘void’
In file included from MainWindow.h:29,
                 from MainWindow.cpp:15:
ACcapture.h:35: error: expected class-name before ‘{’ token
ACcapture.h:36: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
ACcapture.h:38: error: expected ‘;’ before ‘private’
ACcapture.h:41: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcapture.h:41: error: expected ‘;’ before ‘*’ token
ACcapture.h:43: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcapture.h:43: error: expected ‘;’ before ‘*’ token
ACcapture.h:44: error: ISO C++ forbids declaration of ‘QHBoxLayout’ with no type
ACcapture.h:44: error: expected ‘;’ before ‘*’ token
ACcapture.h:46: error: ISO C++ forbids declaration of ‘QGroupBox’ with no type
ACcapture.h:46: error: expected ‘;’ before ‘*’ token
ACcapture.h:48: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcapture.h:48: error: expected ‘;’ before ‘*’ token
ACcapture.h:50: error: ISO C++ forbids declaration of ‘QCheckBox’ with no type
ACcapture.h:50: error: expected ‘;’ before ‘*’ token
ACcapture.h:56: error: ISO C++ forbids declaration of ‘QSpinBox’ with no type
ACcapture.h:56: error: expected ‘;’ before ‘*’ token
ACcapture.h:58: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACcapture.h:58: error: expected ‘;’ before ‘*’ token
ACcapture.h:61: error: ISO C++ forbids declaration of ‘QWebView’ with no type
ACcapture.h:61: error: expected ‘;’ before ‘*’ token
ACcapture.h:63: error: ISO C++ forbids declaration of ‘QPushButton’ with no type
ACcapture.h:63: error: expected ‘;’ before ‘*’ token
ACcapture.h:68: error: expected `:' before ‘slots’
ACcapture.h:69: error: expected primary-expression before ‘void’
ACcapture.h:69: error: ISO C++ forbids declaration of ‘slots’ with no type
ACcapture.h:69: error: expected ‘;’ before ‘void’
In file included from MainWindow.h:30,
                 from MainWindow.cpp:15:
ACattack.h:36: error: expected class-name before ‘{’ token
ACattack.h:37: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
ACattack.h:39: error: expected ‘;’ before ‘private’
ACattack.h:42: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACattack.h:42: error: expected ‘;’ before ‘*’ token
ACattack.h:44: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACattack.h:44: error: expected ‘;’ before ‘*’ token
ACattack.h:45: error: ISO C++ forbids declaration of ‘QHBoxLayout’ with no type
ACattack.h:45: error: expected ‘;’ before ‘*’ token
ACattack.h:47: error: ISO C++ forbids declaration of ‘QGroupBox’ with no type
ACattack.h:47: error: expected ‘;’ before ‘*’ token
ACattack.h:50: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACattack.h:50: error: expected ‘;’ before ‘*’ token
ACattack.h:53: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACattack.h:53: error: expected ‘;’ before ‘*’ token
ACattack.h:54: error: ISO C++ forbids declaration of ‘QLabel’ with no type
ACattack.h:54: error: expected ‘;’ before ‘*’ token
ACattack.h:56: error: ISO C++ forbids declaration of ‘QCheckBox’ with no type
ACattack.h:56: error: expected ‘;’ before ‘*’ token
ACattack.h:58: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACattack.h:58: error: expected ‘;’ before ‘*’ token
ACattack.h:61: error: ISO C++ forbids declaration of ‘QCheckBox’ with no type
ACattack.h:61: error: expected ‘;’ before ‘*’ token
ACattack.h:62: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACattack.h:62: error: expected ‘;’ before ‘*’ token
ACattack.h:64: error: ISO C++ forbids declaration of ‘QLabel’ with no type
ACattack.h:64: error: expected ‘;’ before ‘*’ token
ACattack.h:66: error: ISO C++ forbids declaration of ‘QWebView’ with no type
ACattack.h:66: error: expected ‘;’ before ‘*’ token
ACattack.h:68: error: ISO C++ forbids declaration of ‘QPushButton’ with no type
ACattack.h:68: error: expected ‘;’ before ‘*’ token
ACattack.h:73: error: expected `:' before ‘slots’
ACattack.h:74: error: expected primary-expression before ‘void’
ACattack.h:74: error: ISO C++ forbids declaration of ‘slots’ with no type
ACattack.h:74: error: expected ‘;’ before ‘void’
In file included from MainWindow.h:31,
                 from MainWindow.cpp:15:
ACcrack.h:36: error: expected class-name before ‘{’ token
ACcrack.h:37: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
ACcrack.h:39: error: expected ‘;’ before ‘private’
ACcrack.h:42: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcrack.h:42: error: expected ‘;’ before ‘*’ token
ACcrack.h:44: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcrack.h:44: error: expected ‘;’ before ‘*’ token
ACcrack.h:45: error: ISO C++ forbids declaration of ‘QHBoxLayout’ with no type
ACcrack.h:45: error: expected ‘;’ before ‘*’ token
ACcrack.h:46: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
ACcrack.h:46: error: expected ‘;’ before ‘*’ token
ACcrack.h:48: error: ISO C++ forbids declaration of ‘QGroupBox’ with no type
ACcrack.h:48: error: expected ‘;’ before ‘*’ token
ACcrack.h:50: error: ISO C++ forbids declaration of ‘QCheckBox’ with no type
ACcrack.h:50: error: expected ‘;’ before ‘*’ token
ACcrack.h:56: error: ISO C++ forbids declaration of ‘QComboBox’ with no type
ACcrack.h:56: error: expected ‘;’ before ‘*’ token
ACcrack.h:60: error: ISO C++ forbids declaration of ‘QWebView’ with no type
ACcrack.h:60: error: expected ‘;’ before ‘*’ token
ACcrack.h:62: error: ISO C++ forbids declaration of ‘QPushButton’ with no type
ACcrack.h:62: error: expected ‘;’ before ‘*’ token
ACcrack.h:67: error: expected `:' before ‘slots’
ACcrack.h:68: error: expected primary-expression before ‘void’
ACcrack.h:68: error: ISO C++ forbids declaration of ‘slots’ with no type
ACcrack.h:68: error: expected ‘;’ before ‘void’
In file included from MainWindow.cpp:15:
MainWindow.h:33: error: expected class-name before ‘{’ token
MainWindow.h:34: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
MainWindow.h:36: error: expected ‘;’ before ‘protected’
MainWindow.h:38: error: ISO C++ forbids declaration of ‘QVBoxLayout’ with no type
MainWindow.h:38: error: expected ‘;’ before ‘*’ token
MainWindow.h:39: error: ISO C++ forbids declaration of ‘QTabWidget’ with no type
MainWindow.h:39: error: expected ‘;’ before ‘*’ token
MainWindow.h:49: error: expected `)' before ‘*’ token
In file included from MainWindow.cpp:19:
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
sorcerynet.xpm:21: warning: deprecated conversion from string constant to ‘char*’
MainWindow.cpp:21: error: expected `)' before ‘*’ token
MainWindow.cpp: In member function ‘void MainWindow::welcome()’:
MainWindow.cpp:50: error: ‘QMessageBox’ was not declared in this scope
MainWindow.cpp:51: error: expected type-specifier before ‘QMessageBox’
MainWindow.cpp:51: error: invalid use of member (did you forget the ‘&’ ?)
MainWindow.cpp:51: error: expected `;' before ‘QMessageBox’
MainWindow.cpp:62: error: invalid use of member (did you forget the ‘&’ ?)
MainWindow.cpp:62: error: base operand of ‘->’ is not a pointer
MainWindow.cpp:63: error: type ‘<unresolved overloaded function type>’ argument given to ‘delete’, expected pointer
sorcerynet.xpm: At global scope:
sorcerynet.xpm:2: warning: ‘sorcerynet’ defined but not used
make: *** [MainWindow.o] Error 1

i hope this isn't too much. i'm a little new to ubuntu but i am getting everything straight but their is certain things that i need to learn.

---

### Post by michy99 on 2009-07-19
Was there a configure file? If so what output did you get when you ran it?

---

### Post by hotshot247 on 2009-07-19
no their is no configure file in it. i've never seen something without a configure file before. i'll name all of the files in the folder. 

1. ACattack.cpp
2. ACattack.h
3. ACcapture.cpp
4. ACcapture.h
5. ACcommon.cpp
6. ACcommon.h
7. ACcrack.cpp
8. ACcrack.h
9. ACscan.cpp
10. ACscan.h
11. ACtools.cpp
12. ACtools.h
13. main.cpp
14. MainWindow.cpp
15. MainWindow.h
16. Makefile
17. qaircrack-ng.pro
18. sorcerynet.xpm

what i did to try to compile it was:
# qmake -o Makefile qaircrack-ng.pro
# make

and then after that is when it had all of the errors and warnings.

---

### Post by michy99 on 2009-07-19
According to the Readme file, you have to have QT4 and libv2 installed. I assume you have these?

---

### Post by hotshot247 on 2009-07-20
i remember installing qt4, not sure about libv2. is there a way to check and see if it's installed?

---

### Post by nothingspecial on 2009-07-20
Search for it in synaptic and see if it`s installed

or ```
dpkg --get-selections | grep libv2
```

Bear in mind it might be called lib-v2 or libv.2 or something else.

---

### Post by hotshot247 on 2009-07-20
i checked synaptic package manager and i didn't even see libv2 on the list. i also tried that command that you gave me and it didn't do anything. it took me back to the prompt, nothing else.

---

### Post by nothingspecial on 2009-07-20
> **hotshot247 said:**
> i checked synaptic package manager and i didn't even see libv2 on the list. i also tried that command that you gave me and it didn't do anything. it took me back to the prompt, nothing else.

That command searches to see if you have it installed, it took you back to the prompt because it is not.

You have to get it from [[COLOR="Magenta"]here[/COLOR]]("http://www.sorcerynet.org/")

---

