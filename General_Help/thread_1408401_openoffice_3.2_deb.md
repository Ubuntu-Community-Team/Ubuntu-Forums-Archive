---
title: "openoffice 3.2 deb"
date: 2010-02-16
forum: General Help
---

### Post by KegHead on 2010-02-16
Hi!

Is there a source for a deb file for 3.2?

Thanks!

KegHead

---

### Post by howefield on 2010-02-16
There is a good thread in the forum explaining how to get and install 3.2.

Have a search for it.

I'll have a look but can't quite see it.

There you go...

[http://ubuntuforums.org/showthread.php?t=1404156](http://ubuntuforums.org/showthread.php?t=1404156)

---

### Post by Andy Wilkins on 2010-04-07
The link to the thread is spot on - it's a great help!

---

### Post by jimmers on 2010-04-07
Try This:-

  	 	 	 	 	 	  This tutorial will explain how to install latest version of openoffice in ubuntu
 You can check what is new in openoffice 3.2 from [here]("http://www.openoffice.org/dev_docs/features/3.2/")
  First go to the [OpenOffice website]("http://download.openoffice.org/other.html") and download the Linux .deb file (On your [[COLOR=#006400]_desktop_[/COLOR]]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#"))
 1 - Once you have done that, extract the .deb file,
 [INDENT]OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Run the following command from terminal or just right click select extract
 [INDENT]tar xzvf OOo_3.2.0_LinuxIntel_install_en-GB_deb.tar.gz[/INDENT] Then you’ll see a file called OOO320_m12_native_packed-1_en-GB.9483
 2 - You can remove the existing version of OpenOffice if you wish with this command:
 [INDENT]sudo apt-get remove openoffice*.*[/INDENT] 3 - Copy and paste OOO320_m12_native_packed-1_en-GB.9483 onto the desktop then open Terminal and paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/*.deb[/INDENT] 4 - Then paste this command:
 [INDENT]sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-GB.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb[/INDENT] Once you’ve done that you’ll find OpenOffice 3.2 in Office.


Good Luck


Jim

---

