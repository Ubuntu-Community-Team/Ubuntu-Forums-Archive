---
title: "cannot open uninstaller"
date: 2009-09-29
forum: General Help
---

### Post by saias on 2009-09-29
hi i am trying to open uninstaller and uninstall itunes from wine. 
after typing uninstaller on the terminal i get : 

The program 'uninstaller' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: uninstaller: command not found

i type sudo apt-get install wine

but again the same problem. anu ides to fix it or any other way to uninstall programms from wine?

thanks

---

### Post by MelDJ on 2009-09-29
go to the wine menu, and go to uninstall wine software and you will be able to delete itunes from there

---

### Post by saias on 2009-09-29
i tried that and the itunes uninstaller opens. i am choosing to remove the itunes from the wizard but in the end itunes is still there. 

i never managed to open itunes because it seemed to be an error on the installation. thats why i thought uninstaller whould help me.

---

### Post by MelDJ on 2009-09-29
after you type sudo apt-get install wine, what is the error that comes?

---

### Post by saias on 2009-09-29
i dont get any error it actually says everything is installed:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
The following packages were automatically installed and are no longer required:
  kdelibs4c2a libmd5-perl libgtk2-sexy-perl libcrypt-ssleay-perl
  libxml-namespacesupport-perl kdelibs-data liblualib50 libgtk2-trayicon-perl
  libxml-sax-expat-perl libcrypt-simple-perl libavahi-qt3-1
  libcrypt-blowfish-perl libxml-sax-perl libxml-simple-perl libqt3-mt liblua50
  libsexymm2 libemail-mime-encodings-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by MelDJ on 2009-09-29
this might guide you: [http://ubuntuforums.org/showthread.php?t=59514](http://ubuntuforums.org/showthread.php?t=59514)
hope it hleps

---

### Post by saias on 2009-09-30
I managed to uninstall and reinstall wine. the forum was very helpful.

thanks for the help.

---

