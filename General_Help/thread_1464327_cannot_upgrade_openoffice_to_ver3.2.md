---
title: "cannot upgrade openoffice to ver3.2"
date: 2010-04-28
forum: General Help
---

### Post by creatxr on 2010-04-28
i 've installed *.deb of openoffice 3.2 . but when i start openoffice from menu , it still shows ver 3.1.1 . after it started , it still shows it is ver 3.1.1 in the "about" menu.

---

### Post by scouser73 on 2010-04-28
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file to your desktop

[COLOR="Red"]**NOTICE:**[/COLOR] **Please download the version for your country, and replace** [COLOR="red"]**en-GB.9483**[/COLOR] with [COLOR="red"]**en-US.9483**[/COLOR] **if you live in USA and so on**

Once you have done that, extract the **.deb** file, 

OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz

Then you'll see a file called **OOO320_m12_native_packed-1_en-GB.9483** [COLOR="Red"]**or the file in the language for your country**[/COLOR]

You can remove the existing version of OpenOffice if you wish with this command: 

**> sudo apt-get remove openoffice*.***

Copy and paste this command into the Terminal

> **sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb**

Then paste this command: 

**> sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-**.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb**

Once you've done that you'll find OpenOffice 3.2 in Office.

---

