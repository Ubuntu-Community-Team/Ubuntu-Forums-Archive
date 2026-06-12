---
title: "Newbie trying the switch to Ubuntu from Windows"
date: 2011-04-17
forum: General Help
---

### Post by newbun on 2011-04-17
Hi Forum

I have the latest version of Ubuntu (10.10?) on a USB stick.  I know its possible to boot up a Windows machine and direct the process to boot from the stick - could you refresh my memory?

My reason for doing the alternate boot is to give Ubuntu a trial run (from the stick) without actually altering my file system.

I'm sure the forum members can provide a step by step process for the alternate boot?

I'm currently running Windows XP,  but I could switch to Ubuntu if the system suits my needs.

Hope you can help?;)

Thanks and looking forwward to your replies.

---

### Post by Linux_junkie on 2011-04-17
To boot from a bootable USB stick you'll probably have to press the F12 key as soon as you switch on your computer during the BIOS setup.  It should give you a menu to select which drive to boot from which you select USB.

That should be it.  If any problems let us know.

---

### Post by Paqman on 2011-04-17
Exactly how to get your machine to boot from a USB stick depends on your machine, but in general you have to change the boot order in your BIOS. To access you BIOS look for something on screen as soon as you power on telling you to hit something like delete, F1, F2, etc. You'll only have a couple of seconds to hit the button to stop it booting. Some BIOSs will have a different button to hit just for changing the boot priority.

---

### Post by ssulaco on 2011-04-17
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

> Booting the Computer from USB
Insert the bootable USB flash drive that you just created in your target computer, and restart it. Most newer computers can boot from a USB drive. If your computer does not automatically do so, you might need to edit the BIOS settings.

Restart your computer, and watch for a message telling you which key to press to enter the BIOS setup. It will usually be one of F1, F2, DEL, ESC or F10. Press this key while your computer is booting to edit your BIOS settings. (On HP Mini Netbooks, they correct key is usually F9.)

Instead of editing BIOS settings, you can chose boot device from boot menu. Press function key to enter boot menu when your computer is booting. Typically, boot screen display which key that you need. It maybe one of F12, F10. Note: in some mainboard, you have to chose 'hard disk/USB-HDD0' for USB flash disk.

You need to edit the Boot Order. Depending on your computer, and how your USB key was formatted, you should see an entry for "removable drive" or "USB media". Move this to the top of the list to force the computer to attempt to boot from USB before booting from the hard disk.

.......once booted,youll want "try Ubuntu without any changes to your computer"

---

### Post by walt.smith1960 on 2011-04-17
I don't know how widespread my experience with USB drives are but I've tried Unetbootin & Startup Disk Creator.  I've tried different .iso s on a couple different USB drives.  The same USB drive will boot fine on a ThinkPad R61 and homebuilt machine using a Gigabyte AMD 740 chipset MB. On another homebuilt machine using a Gigabyte AMD 785 chipset I get a message to the effect of "no boot sector".  The 785 based machine's BIOS setting seems right, it sees the USB drive but won't load.    All 3 machines work fine with CD's created from .iso files but they're S L O W to load and there's no persistence possible.  Just a heads-up to perhaps save some "What am I doing wrong?" moments :)

---

### Post by madjr on 2011-04-17
> **newbun said:**
> Hi Forum

I have the latest version of Ubuntu (10.10?) on a USB stick.  I know its possible to boot up a Windows machine and direct the process to boot from the stick - could you refresh my memory?

My reason for doing the alternate boot is to give Ubuntu a trial run (from the stick) without actually altering my file system.

I'm sure the forum members can provide a step by step process for the alternate boot?

I'm currently running Windows XP,  but I could switch to Ubuntu if the system suits my needs.

Hope you can help?;)

Thanks and looking forwward to your replies.

if you decide to install it, it will keep your windows XP just as it is now.

you dont need to give up one for the other, you can have them both! And is recommended too, in case XP fails, gets a virus, etc.

installing is very easy and takes like 25 minutes.

once installed, you can try it out for real, install programs, etc.

Trying it from USB or CD is just to see if the hardware works, not much else. And are very slow compared to a real install.

so if everything works, go ahead :)

heres a good guide for you to get started:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

then you might want to customize it a bit :)
[http://news.softpedia.com/news/Ubuntu-10-10-Desktop-Customization-Guide-186408.shtml](http://news.softpedia.com/news/Ubuntu-10-10-Desktop-Customization-Guide-186408.shtml)

---

### Post by newbun on 2011-04-18
Well!  Thank you, Linux_junkie, Paqman, ssulaco, walt.smith1960,and madjr.  You've all been totally helpful.  :D  

I'll follow your instructions and report back.....

---

### Post by Johnsie on 2011-04-18
Hi, I find the Wubi.exe tool on the live cd/usb extremely useful. It installs Ubuntu from Windows without messing around with partitioning. If you want to be able to uninstall ubuntu later then that is a good way to do it. To Uninstall a wubi install of Ubuntu you just go into Windows Control Panel and remove it just like any other Windows program. I do a Wubi install on nearly every computer I work with (as a backup in case Windows fails)

A wubi install is a little slower than a proper install, but it's a good way for people to get to know the OS without committing to anything.

---

### Post by philinux on 2011-04-18
Thread moved to General Help forum.

---

### Post by newbun on 2011-04-19
Ok.  The current state of play.  As said previously, I have the 'bootable' Ubuntu 10.10 on a stick.  Luckily my laptop has the USB option higher up the boot order than the hard drive where the Windows system resides, so I didn't need to hit the F2 button...but I was poised ready - thanks to the forum members.
Up came the TRY UBUNTU,  INSTALL screen, so I chose 'TRY'.:)

I browsed online using the installed Firefox 3.6.10, but I believe that 4.0 is out there, should I wish to download it.  First impressions are that the system (even from the stick) seems a little swifter than Windows - I don't know if I'm imagining it.  Opened a few spreadsheet & doc files - seemed ok.
Also tried iPlayer, but apparently I need some flash download, but wasn't sure where (on the system) it would go, since I'm 'trying out' Ubuntu. I guess if I installed it alongside Windows, it would be placed in THAT section of the file system?

iPlayer works fine on Windows.

So, from these tentative steps, I think I'll install a parallel operating system and, who knows, I may opt to permanently use Ubuntu.

Thanks again Forum - you've been a great help.  If I have any future queries on Ubuntu, I'll know where to come for clear instructions:)

Oh, did I say I'm posting this from the 'new' system?

---

### Post by madjr on 2011-04-19
> **newbun said:**
> Ok.  The current state of play.  As said previously, I have the 'bootable' Ubuntu 10.10 on a stick.  Luckily my laptop has the USB option higher up the boot order than the hard drive where the Windows system resides, so I didn't need to hit the F2 button...but I was poised ready - thanks to the forum members.
Up came the TRY UBUNTU,  INSTALL screen, so I chose 'TRY'.:)

I browsed online using the installed Firefox 3.6.10, but I believe that 4.0 is out there, should I wish to download it.  First impressions are that the system (even from the stick) seems a little swifter than Windows - I don't know if I'm imagining it.  Opened a few spreadsheet & doc files - seemed ok.
Also tried iPlayer, but apparently I need some flash download, but wasn't sure where (on the system) it would go, since I'm 'trying out' Ubuntu. I guess if I installed it alongside Windows, it would be placed in THAT section of the file system?

iPlayer works fine on Windows.

So, from these tentative steps, I think I'll install a parallel operating system and, who knows, I may opt to permanently use Ubuntu.

Thanks again Forum - you've been a great help.  If I have any future queries on Ubuntu, I'll know where to come for clear instructions:)

Oh, did I say I'm posting this from the 'new' system?

good to see you are already liking it :)

as for flash you can install it from the adobe website or from the ubuntu software center.

these should be useful:

[http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/](http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.youtube.com/watch?v=16Ocb8oNhM8](http://www.youtube.com/watch?v=16Ocb8oNhM8)

have fun :D

---

### Post by newbun on 2011-04-22
Having previously 'tried' Ubuntu 10.10, I'm now at the stage where I'm about to TRY it on a desktop - currently running  (7.04 feisty?).

I booted from a freshly prepared CD, got to the 'Ubuntu 10.10' screen with the alternating dots , until it finally arrived at the 'Username:' then 'password' screen??  This is a NEW install, why is it asking me for details I didn't set??
[THIS PAGE: TROUBLES WITH LIVE CD]("https://help.ubuntu.com/community/LiveCD"): 
is similar to what's displayed.  It suggests that I 'let it timeout' of hit return.  Neither of which worked, and there was no timeout countdown on my screen.  The result was 'authentification failure' on both those suggestions, in addition a few I tried myself.

Any ideas please?

---

### Post by SeijiSensei on 2011-04-22
Check your BIOS and make sure the CD-ROM comes before the hard drive in the list of boot devices.  There may also be a key you can press during startup that allows you to choose the boot device.

---

### Post by anandkumar44 on 2011-04-22
Welcome to the world of Ubuntu.
Just take a look at this link 
[COLOR=Blue]**[http://theindexer.wordpress.com/2010/10/02/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://theindexer.wordpress.com/2010/10/02/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)**[/COLOR]

---

### Post by newbun on 2011-04-22
> **SeijiSensei said:**
> Check your BIOS and make sure the CD-ROM comes before the hard drive in the list of boot devices.  ..

On THIS particular desktop, DEL, is the key to hit during the boot process.  I've put the CD-ROM first in the boot order.  The hard drive is currently 3rd....

---

### Post by dino99 on 2011-04-22
classic howto:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rebelli0us on 2011-04-22
welcome to UBU land. USB stick works fine but is slower, USB flash speed is ~10 MB/sec hard disk is ~75 to 100+ MB/sec

---

### Post by newbun on 2011-04-22
Curiouser and curiouser!  I tried booting from the SAME CD on a laptop, and went straight through to the INSTALL / TRY option.

I have 1gb of RAM and a free 6gb of drive, would that be a problem on said laptop, IF, I decide to install alongside (windows)?

---

