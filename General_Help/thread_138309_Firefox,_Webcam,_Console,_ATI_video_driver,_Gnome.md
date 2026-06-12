---
title: "Firefox, Webcam, Console, ATI video driver, Gnome"
date: 2006-03-01
forum: General Help
---

### Post by Qwertie on 2006-03-01
Note: I'm using KDE but my questions are mostly not KDE-specific.

I'm a newbie with several questions:

**1.** There was no Firefox 1.5 package so I did a crude installation loosely based on some extremely intricate Ubuntu-specific instructions (I don't have the URL now).  Anyway, Firefox is ugly:
[IMG]http://static.flickr.com/25/103562862_c9a3fac428_o.png[/IMG]
Notice the somewhat ugly font in the menu bar.  How can I change the font, and lighten the black lines between toolbars?

**2.** In Firefox, the middle mouse button opens an apparently random web site.  How can I use the middle button as a sticky scroll button like in Windows?  I couldn't find an applicable option in Edit | Preferences.

**3.** How can I use a webcam under Linux?  Is there any webcam-supporting IM program? (Kubuntu System Settings shows my webcam under "Digital Camera": a D-Link DSC 350+, but when I click the link to camera://D-Link DSC 350+@[usb:003,003]/ in Konqueror, I get the following error message after many seconds have passed: The process for the camera://usb:003,003 protocol died unexpectedly.)

**4.** How do I configure the console so that Tab completes filenames?

**5.** I'm having trouble installing the ATI Radeon proprietary driver.  After downloading from [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27"), and installing in "express" mode, the instructions at [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html") say to do

/usr/X11R6/bin/aticonfig --initial

but here's what happens:

root@computilo:/home/david/DL# /usr/X11R6/bin/aticonfig --initial
/usr/X11R6/bin/aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

**6.** How to I get Gnome in Kubuntu, and all that stuff Ubuntu has?  You know, like, a Ku-Ubuntu.  Ubuntu gets better support so I'd like to have it; also, I want the Gnome control panels in order to customize those (ahem) not completely beautiful Gnome windows.

---

### Post by deathbyswiftwind on 2006-03-01
Alright well first here is a great howto for the ati cards. [http://www.ubuntuforums.org/showthread.php?t=75378&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=howto+ati) works everytime for my system.

Second as far as your install of firefox did you use apt-get? If you dont know how to use apt-get please let me know and ill explain it. Its one of the main "selling" points of ubuntu i think.

As far as getting ubuntu in kubuntu Id recommend downloading the ubuntu cds(dvd) and install Ubuntu then apt-get install kde. It installs a slightly older version of kde which has been more refined then Kubuntu which is a newer less updated version. I myself cannot use Kubuntu because that version of kde has an issue with my comp but by install Ubunutu and then apt getting the kde it works perfect.

As far as the webcam and changing the mouse button I dont know. As far as the fonts download a new theme for firefox. Im sure you could find at least one you like.

If you have any questions feel free to ask and welcome to the best damn distro of linux around

---

