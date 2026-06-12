---
title: "T mobile dongle 120 MF262"
date: 2011-07-17
forum: General Help
---

### Post by gazza1976 on 2011-07-17
Hi,
 
Im having a lot of trouble getting my t mobile dongle to work. I have looked through most of the other threads about resolving the problem. Is there a easyifx to this issue? I am new to computing so when I see the answer sbout typing comands into the terminal I get lost and dont know what to do...
 
I now have ubuntu 10.04 and 11.04 duel boot on laptop (hp nx6325).
 
Cant seem to get it work on either virsion. I have tryed to chance passwords as other threads have sugested.
 
Am now trying (and failing) with this thread [http://ubuntuforums.org/showthread.php?t=1147685](http://ubuntuforums.org/showthread.php?t=1147685)
 
I have downloaded the mode switch and extracted it to the desktop.
 
In the above thread it say "3) Open the Terminal, and go to the location of the decompressed file and execute"
 
What does it mean go to the location? Can somebody help please?
 
Many thanks.

---

### Post by Swagman on 2011-07-17
> In the above thread it say "3) Open the Terminal, and go to the location of the decompressed file and execute"

It means... open a terminal (shortcut) press ctrl + alt + t

you now have a terminal open. So to navigate to the desktop the easy way type cd (press spacebar) then drag your desktop folder (where you unpacked your file) into the terminal and press enter... bingo..  the terminal is now looking in the folder on your desktop.

If it's just the  desktop you want (no folder) type cd /home/gazza1976/Desktop (press Enter)

gazza1076 being whatever your username is, eg: mine is paul so that would be cd /home/paul/Desktop

But if you have followed all the other steps and you have the unzipped file on your desktop..right click the file and select properties/permissions and tick "allow executing file as program" close it and now you should be able to just double click on the icon to run it

---

### Post by gandaran on 2011-07-17
> **gazza1976 said:**
> Hi,
 
Im having a lot of trouble getting my t mobile dongle to work. I have looked through most of the other threads about resolving the problem. Is there a easyifx to this issue? I am new to computing so when I see the answer sbout typing comands into the terminal I get lost and dont know what to do...
 
I now have ubuntu 10.04 and 11.04 duel boot on laptop (hp nx6325).
 
Cant seem to get it work on either virsion. I have tryed to chance passwords as other threads have sugested.
 
Am now trying (and failing) with this thread [http://ubuntuforums.org/showthread.php?t=1147685](http://ubuntuforums.org/showthread.php?t=1147685)
 
I have downloaded the mode switch and extracted it to the desktop.
 
In the above thread it say "3) Open the Terminal, and go to the location of the decompressed file and execute"
 
What does it mean go to the location? Can somebody help please?
 
Many thanks.
on ubuntu 10.04 you need to install usb-modeswitch (it's installed by default on Ubuntu 11.04) but threes no need to download any file, if you can connect to wired internet just find the usb-modeswitch package in synaptic package manager then mark for install and click the apply button, that's how easy it is to install packages on Ubuntu, forget the hard way compiling stuff.
also you just need to run the mobile setup wizard, choose your country and internet provider, check that ISP login authentication details are correct then you modem should just work, its all very easy using mobile broadband on Ubuntu.

---

### Post by ieee488 on 2011-07-17
> **gazza1976 said:**
> Hi,
 
Im having a lot of trouble getting my t mobile dongle to work. I have looked through most of the other threads about resolving the problem. Is there a easyifx to this issue? I am new to computing so when I see the answer sbout typing comands into the terminal I get lost and dont know what to do...
 


I found that my T-mobile USB device was recognized in 11.04.

Plug it in first, then turn on laptop.

---

