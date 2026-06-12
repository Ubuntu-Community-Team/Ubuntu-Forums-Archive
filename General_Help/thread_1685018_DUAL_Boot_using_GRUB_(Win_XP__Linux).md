---
title: "DUAL Boot using GRUB (Win XP / Linux)"
date: 2011-02-10
forum: General Help
---

### Post by nam5301 on 2011-02-10
**BIOS DEVICE BOOT ORDER**
Image link: [http://img809.imageshack.us/img809/5100/biosbootorder.jpg](http://img809.imageshack.us/img809/5100/biosbootorder.jpg)

**DEVICE STARTUP SCREEN**
Image Link:  [http://img140.imageshack.us/img140/327/pcstartupscreen.jpg](http://img140.imageshack.us/img140/327/pcstartupscreen.jpg)

**WINDOWS IN GRUB MENU**
Image link: [http://img708.imageshack.us/img708/2586/bootorder2.jpg](http://img708.imageshack.us/img708/2586/bootorder2.jpg)

**GRUB MENU.LST**
Image Link: [http://img573.imageshack.us/img573/6056/grub.jpg](http://img573.imageshack.us/img573/6056/grub.jpg)

**GRUB MENU**
Image Link: [http://img638.imageshack.us/img638/1383/grubbootmenu.jpg](http://img638.imageshack.us/img638/1383/grubbootmenu.jpg)

**WINDOWS STARTUP (THIS SCREEN FREEZE LIKE HERE, DOES NOT LOAD WIN XP)**
Image Link:  [http://img96.imageshack.us/img96/628/winxpstartup.jpg](http://img96.imageshack.us/img96/628/winxpstartup.jpg)

This is typed for Backtrack and Windows but I am also trying to do the same thing (DUAL BOOT) for Ubuntu 10.10 Linux with Windows XP, but it has the same problem as below.  Can someone please help if you know the solution?

Okay, so I am really having a hard time with configuring DUAL BOOT for Backtrack and Windows XP.  Each are installed on its own physical hard drive (Both IDE).  Windows XP is installed on MAXTOR 6L020J1-(PM).  While Backtrack is installed in WDC AC310000D- (SS) <--western digital HDD.  I set the first boot as WDC AC310000D-(SS) which is where Backtrack is installed in order to gain access to GRUB Boot Menu.  Because I want to be able to choose which operating system I want to boot from the Menu's list.  But I can't get it to work.  The current configuration are shown on those image links above.  I have the MAXTOR HDD set has (hd1,0) which is correct (i think) because it displays the "Starting Up" screen before it loads the Windows XP startup logo.  But the problem is that the "starting up" screen just hangs there and does not load anything after that.  Not sure what the problem is.  
If anyone who is good at GRUB, please lead me to the way to the land of solutions, where the water is clear and the sky is blue, and where Linux, Apple, Windows hold hands.

---

### Post by oldfred on 2011-02-10
You may need map commands with grub legacy. (mapdevice in grub2)

One real advantage of Ubuntu & grub2 is the osprober almost always finds other systems and lets you boot them. Older versions of grub2 sometimes did not totaly convert other systems boot from grub legacy, but only needed minor tweaking.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

