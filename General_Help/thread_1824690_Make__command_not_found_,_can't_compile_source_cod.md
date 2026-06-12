---
title: "Make : command not found , can't compile source code."
date: 2011-08-14
forum: General Help
---

### Post by al1x on 2011-08-14
Hello there, I 've encountered a problem when I tried to compile source code using the command make.I want to install the QGRUBeditor wich comes with a tar.bz2 file.I read the INSTALL file and it tells me to execute the following commands:
1.qmake-qt4 
2.make
3.sudo make install

Though , when I try to execute make the terminal prints the following message-error:
```
/usr/bin/uic-qt4 ui/about.ui -o build/ui/ui_about.h
make: /usr/bin/uic-qt4: Command not found
make: *** [build/ui/ui_about.h] Error 127
```

I have install build-essential, gcc compiler and the make command...Can you help me please?

---

### Post by al1x on 2011-08-21
Can anyone help me giving a reply? Please?

---

### Post by dino99 on 2011-08-21
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by ron999 on 2011-08-21
Hi
The instructions on the QGRUBEditor website says:-
qmake
make
sudo make install

[http://qt-apps.org/content/show.php/QGRUBEditor?content=60391]("http://qt-apps.org/content/show.php/QGRUBEditor?content=60391")

---

### Post by al1x on 2011-09-05
> **dino99 said:**
> [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I read the documentation but it didn't help me...Can you explain me the error I have posted? Is there any package except build-essential that I must install?

---

### Post by al1x on 2011-09-05
> **ron999 said:**
> Hi
The instructions on the QGRUBEditor website says:-
qmake
make
sudo make install

[http://qt-apps.org/content/show.php/QGRUBEditor?content=60391]("http://qt-apps.org/content/show.php/QGRUBEditor?content=60391")

The INSTALL file consults to execute the command qmake-qt4 rather than qmake.I don't know if there is any difference...
Any way I visited the link you've posted and I remembered that I hadn't install the dependencies and that's why I couldn't compile it!Thank's for the help!:popcorn:

---

