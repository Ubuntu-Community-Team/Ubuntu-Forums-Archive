---
title: "Need Help on Installing Graphics Driver for VIA MB"
date: 2009-06-27
forum: General Help
---

### Post by snooktarpon on 2009-06-27
I have a VIA EPIA ME6000 LVDS Mini-ITX motherboard. Here are the specs: [http://www.wdlsystems.com/downloads/specs/1EPME60_s.pdf](http://www.wdlsystems.com/downloads/specs/1EPME60_s.pdf)

I installed 9.04 Desktop. Everything is working fine expect for the the monitor resolution. I'm limited to 640x480 or 800x600. So I need to install the graphics driver so I can have higher resolutions. BTW, this is my first time using the Linux platform.

I went to the VIA driver web page at: [http://www.viaarena.com/default.aspx?PageID=2](http://www.viaarena.com/default.aspx?PageID=2)
From there I select: Ubuntu Linux -> Integrated Graphics -> CLE266 Unichrome Integrated Graphics
This takes you this web page where you have several driver variants (binary and source code) to choose from:
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=101](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=101)

Well, downloaded the first driver listed (VIA UniChrome Pro Driver Binary for Ubuntu 7.10) which downloads the following files: via_ubuntu710.unichrome-v40072d-kernal-bin-_v0.80.zip
The file contains 3 files: 
- installation.txt
- readme.pdf
- VIA_U710_UniChrome-GFX-v40072d.run.

 I briefly read the txt and pdf files but I did not understand all the instructions. So I double-clicked on the .run file but then I get error message: Could not open the file ...

So can someone please help me install graphics drivers for my system?

Sincerely,
Jim

---

### Post by QIII on 2009-06-27
Before you do anything, save any important files.  If you don't have any (say you just installed), so much the better.  If you haven't tinkered with anything, the worst you will have to do is reinstall Jaunty.  But let's hope it doesn't come to that.

I can't tell you what to expect for a drive built for 7.10  -- which I'm not sure is even supported any longer.  Is there one for 9.04?

If not, it may still be worth a try, as long as you can afford to reinstall Jaunty...

Cut and paste my instructions below, put them in a text file and print it off before you start. Once you kill the Gnome Desktop Manager, you won't be able to see this.

Make sure that VIA_U710_UniChrome-GFX-v40072d.run is on your desktop.

Press CTL-ALT-F2 to close the window session.
Type in your username and password when prompted.
In the command line, type

sudo /etc/init.d/gdm stop
sudo sh ~/VIA_U710_UniChrome-GFX-v40072d.run
     -- Follow the instructions in your readme or what is displayed on screen
sudo /etc/init.d/gdm restart

Please post back how this works.

---

### Post by snooktarpon on 2009-06-29
QIII,

Thanks for the reply. I followed your directions and I unfortunately, I get a error message stating the following:

Please choose the job you want to do:
1. Install driver
2. Uninstall driver

So I selected "1"
and received the following output:

====== VIA Unichrom (Pro) Family Display Driver for Unbuntu 7.10 ======
====== Installation Program ======
Errror:
  This driver package is only for the default kernel
  " 2.6.22-14-generic" for Ubuntu 7.10

Then it takes back to the command prompt. BTW, there is not a driver for version 9.04 on the VIA website. 7.10 is the latest.

So I'm I screwed? I just want to have a display resolution greater then 800x600.

---

### Post by snooktarpon on 2009-07-05
I posted this question on the VIA forums without any success. 

All I want is to have a greater screen resolution then 800x600 with Ubuntu.

If I cannot find a VIA graphics driver for Ubuntu 9.04, are there any other options?

Otherwise, I'm going to have to use XP (since graphics drivers exist for XP).

---

