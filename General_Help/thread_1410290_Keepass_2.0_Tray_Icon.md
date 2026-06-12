---
title: "Keepass 2.0 Tray Icon"
date: 2010-02-18
forum: General Help
---

### Post by Calcipher on 2010-02-18
Hello, I am having a strange problem.  I am using KeePass 2.09 portable on several machines (three Windows, two linux) and one of them is not functioning properly.  As I mentioned, I have two Linux (Ubuntu 9.10) boxes, on one of them the following mono install:
```

(Output of dpkg --get-selections | grep -i mono)
libmono-accessibility1.0-cil			install
libmono-accessibility2.0-cil			install
libmono-addins-gui0.2-cil			install
libmono-addins0.2-cil				install
libmono-cairo2.0-cil				install
libmono-corlib1.0-cil				install
libmono-corlib2.0-cil				install
libmono-data-tds1.0-cil				install
libmono-data-tds2.0-cil				install
libmono-i18n-west1.0-cil			install
libmono-i18n-west2.0-cil			install
libmono-posix1.0-cil				install
libmono-posix2.0-cil				install
libmono-security1.0-cil				install
libmono-security2.0-cil				install
libmono-sharpzip2.84-cil			install
libmono-sqlite2.0-cil				install
libmono-system-data1.0-cil			install
libmono-system-data2.0-cil			install
libmono-system-web1.0-cil			install
libmono-system-web2.0-cil			install
libmono-system1.0-cil				install
libmono-system2.0-cil				install
libmono-webbrowser0.5-cil			install
libmono-winforms1.0-cil				install
libmono-winforms2.0-cil				install
libmono0					deinstall
libmono2.0-cil					install
mono-2.0-gac					install
mono-gac					install
mono-mcs					install
mono-runtime					install

```
I duplicated this install to my other Ubuntu box with the exception of libmono0 not being marked as deinstall (not sure how that happened).  The thing is that on the box (which the dump came from) the KeePass tray icon shows up while on the other one the tray icon does not show up.  I need the tray icon in order to lock/unlock the program. 

Any ideas?

---

### Post by bodhi.zazen on 2010-02-18
I know it does not answer your question, but ...

I use keepassx on Linux and version 1 on a portable drive.

I found version 2 to be buggy last time I tried it and I am satisfied with the security of version 1.

You may keep the data on a portable driver and use the data base with keypassx on Fedora or Ubuntu and launch the portable application on any windows box.

As you are using a 3rd party application you will likely get a better answer if you use the keypass support.

---

