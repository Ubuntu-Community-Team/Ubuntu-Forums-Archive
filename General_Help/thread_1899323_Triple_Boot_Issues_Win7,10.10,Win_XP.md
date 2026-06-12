---
title: "Triple Boot Issues Win7,10.10,Win XP"
date: 2011-12-23
forum: General Help
---

### Post by TheDevilYouKnow on 2011-12-23
Hello Guys and Gals!

I have an interesting and puzzling problem here...

I have created a successful triple booting system with Windows 7,Ubuntu 10.10,and Windows XP. I did that BEFORE I just recently upgraded most of my hardware including my Motherboard,RAM (16 Gb up from 8),video card,processor and monitor.I am using GRUB 2 as my boot loader.Ubuntu is now clearly broken,as it does boot but now needs a partial upgrade ( considering upgrading all the way to 11.10 with all this new hardware...maybe ) and many updates. Windows XP does not boot however and gives me the old :

BOOTMGR is missing - press CTRL-ALT-DELETE to restart.

arrrgh.

I have placed the hard drive boot priorities in the proper order so that the system boots to the GRUB flawlessly but I am lost on the proper method to repair XP in this configuration.


Can a brotha get a little help please?


Any input is greatly Appreciated!

---

### Post by BC59 on 2011-12-23
I was just wondering for what purpose you could need WinXP....

---

### Post by Mark Phelps on 2011-12-23
That's a Win7 boot error message.  XP did not use Bootmgr; instead, it used NTLDR.  If it was an XP boot error, it would say something about not being able to find NTLDR.

IF you had XP on your box and THEN installed Win7, it's nearly certain that Win7 reused the XP partition and wrote its boot loader files there.

Changing out the motherboard (and other hardware) and then simply plugging in a hard drive with a previous install of Windows almost always will not work well -- because Windows will attempt to load using the wrong (old) drivers.

You will need to, at a minimum, repair your Win7 booting -- and possibly upgrade your Win7 drivers as well, AND , your XP drivers, too.

Since these are purely Windows problems, I suggest you check with the Windows 7 forum (sevenforums.com) about how to do this effectively.

Once you get your Windows versions up and running, come back here and we'll tell you how to get GRUB back working as well.

---

### Post by BC59 on 2011-12-23
You can check here

[http://www.techspot.com/guides/143-dual-boot-windows7/](http://www.techspot.com/guides/143-dual-boot-windows7/)

and here

[http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html](http://www.sevenforums.com/tutorials/8057-dual-boot-installation-windows-7-xp.html)

how you could do it. 
As @Mark Phelps said it's not that easy, so I suggest you to rethink it, because I don't find why you should do that dual boot. Windows 7 can run all WinXP programs and as I can see your computer is fast enough to run Win7 decently.

---

### Post by TheDevilYouKnow on 2011-12-23
Thank you all so much for all the help so far!

Let me describe what happens when I boot up an dtry to answer some of your questions.

When I boot my machine displays all the POST information as normal,then GRUB comes up showing my Ubuntu,Windows 7,and Windows XP options as normal. When I choose XP 
I get the error. Windows 7 boots up when I choose it in GRUB with no issues what-so-ever.

I already have updated/re-installed all the new and necessary drivers ( for Windows 7 anyway )...Still have to work on Ubuntu...and XP...lol. I will try out the methods listed above and post back with results...

I am running XP because of an old program that requires it to run properly ( Dundjinni - don't laugh! I know a few of you still play Dungeons and Dragons ).

Having already looked at Sevenforums I think using Easy BCD might be the answer to my problem. As I stated before my Tripleboot worked perfectly before the hardware upgrades so BOOTMGR being an element of W7 makes sense as a symptom.

I also need to point out that Windows 7 lives on a WD Raptor 72 Gb by itself, that Ubuntu and XP share a 500 Gb WD, and there is a 1 Tb WD that both the other drives have access to as a data drive. The system boots from the drive that Ubuntu and XP are on via the GRUB.

---

### Post by Mark Phelps on 2011-12-23
> **TheDevilYouKnow said:**
> The system boots from the drive that Ubuntu and XP are on via the GRUB.

OK, then what you should be able to do (in Win7) is use EasyBCD, click the Add new Entry button and see if XP is listed in the drop down.  IF it's not, you might still be able to add it manually.

Then, when you boot next into Win7, you will get a menu allowing you to choose between Win7 and XP.

Also, trying to do this in GRUB probably won't work because GRUB will simply hand off control to the windows boot loader in the partition identified in the config file -- in this case, that would be the Win7 boot loader (since it's likely installed in the XP partition).

---

### Post by oldfred on 2011-12-23
Some info on how Windows works.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

If grub is showing both entries for Windows you must still have boot files in both partitions. Normally a second install of Windows copies/moves its boot files to the bootable primary NTFS partition with the boot flag. With multiple drives it may depend on how you installed. If you moved drives around it may just be the boot.ini settings as that is hard coded to drive number.

---

### Post by TheDevilYouKnow on 2011-12-23
When I installed XP I had disconnected the W7 drive COMPLETELY. The only drive in the system at that time was the drive with Ubuntu installed and booting from GRUB. With only that drive connected I then resized the UBUNTU partition to make space for XP...the made the XP installation. Reconnected the W7 drive and Grub picked it right up. So now I am thinking if I disconnect the W7 drive and run FIXBOOT from the XP cd...then reconnect the W7 drive and run easy BCD to see if XP even shows up...am I on the right track?

---

### Post by oldfred on 2011-12-23
If you run the XP repair commands on the XP drive grub will pick it up and you do not need EasyBCD unless you want to have two levels of choices for XP.

You may need more than fixBoot. And drive order becomes important for XP's boot.ini. Windows 7 seems to use something like UUIDs so it is less important.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

