---
title: "Installing Opera?"
date: 2005-02-05
forum: General Help
---

### Post by KoolDrew on 2005-02-05
How exactly do I install it?  I downloaded the tar.gz, but have no idea how to install it.

---

### Post by Quest-Master on 2005-02-05
Untar it, go to the directory it is in, open a terminal in there, and type in 

./configure
make
sudo make install

Should work. There were Opera .deb files on the site though.. you could've just downloaded those and did a:

dpkg -i operadebnamehere.deb

---

### Post by Xian on 2005-02-05
Go to the [Opera Download](http://www.opera.com/download/) website and choose "Debian" from the drop-down menu. Next, tick the box next to "Debian 3.1" and select a download mirror of your liking. After you download the file just open a terminal and cd to the location. Then you just issue the install command:

dpkg -i <filename>

Don't forget you will also need to make sure the libqt-mt and libstdc packages are installed.

---

### Post by KoolDrew on 2005-02-05
[QUOTE=Xian]Go to the [Opera Download](http://www.opera.com/download/) website and choose "Debian" from the drop-down menu. Next, tick the box next to "Debian 3.1" and select a download mirror of your liking. After you download the file just open a terminal and cd to the location. Then you just issue the install command:

dpkg -i <filename>

Don't forget you will also need to make sure the libqt-mt and libstdc packages are installed.[/QUOTE]
 I run **sudo dpkg -i opera_7.54-20050131.5-shared-qt_en_sarge_i386.deb**, but it says this:

```
(Reading database ... 64807 files and directories currently installed.)
Preparing to replace opera 7.54-20050131.5 (using opera_7.54-20050131.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not configured yet.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

```

---

### Post by Xian on 2005-02-05
[QUOTE=KoolDrew]I run **sudo dpkg -i opera_7.54-20050131.5-shared-qt_en_sarge_i386.deb**, but it says this:[/QUOTE]
I did mention this..... :)
```
sudo apt-get install libqt3c102-mt
```

---

