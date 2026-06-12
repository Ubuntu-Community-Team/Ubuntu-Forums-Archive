---
title: "4 primary partitions on an HP laptop."
date: 2011-07-13
forum: General Help
---

### Post by Veren on 2011-07-13
Hello there fellow geeks,
I've been really glad to have my girlfriend willing to try Ubuntu. The problem is that on her HP Pavilion d6something, there are 4 partitions by default, that is:
[B]
-100meg SYSTEM (bootloader)
-470gig (now 370gig) /C:
-about 22gig RECOVERY
-about 100meg HP_TOOLS[/B]

I wasn't there when the Windows was installed, I believe it all is a factory default setting. I have shrunk the /C: from 470 to 370gig using gparted from a live CD of Natty so as to make some space. 

My question is this, is it **safe** for us to delete the third or fourth partition ? She has never created recovery DVDs, but I have some Windows at hand just in case anything goes horribly wrong later on.

The HP_TOOLS has some folders with titles centered around BIOS, but I believe it is just some loading screens with HP logos.

Were it my computer, I wouldn't probably ask at all, but I don't want her to lose any data at all. I was dying a little inside while shrinking the /C: to be honest.

Any help would be greatly appreciated, thank you.

---

### Post by Mark Phelps on 2011-07-13
Did you try rebooting her PC into Win7 to see if it still works?  If it does, you are very lucky -- shrinking a Win7 OS partition with GParted often results in filesystem corruption.

The NEXT thing you should do is boot into Win7 on her PC and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later, should you need to repair the Win7 boot loader.

If the PC has an option to create Restore CDs (probably a DVD nowadays), then do that BEFORE you attempt an Ubuntu install.  Once you do that, you should be able to remove the Recovery partition and use that space for installing Ubuntu.

---

### Post by Veren on 2011-07-13
Yes, I booted just fine right before I left and it worked ok in the evening too. But I know, we were very lucky :P. It also worked this morning, and the initial disk check went fine :)

I also ran chkdsk afterwards just in case.

---

### Post by Veren on 2011-07-13
The problem is not that we don't have enough space, it is that we don't have enough primary partitions :( In fact, say we wouldn't do the backuping - wouldn't we need that only in a case, where it would end up with formating the laptop anyways ? I mean, I have a Windows CD at hand, were it needed to reinstall. I just don't know, whether I can afford to delete the partition.

---

### Post by Veren on 2011-07-13
What if I copied the stuff from HP_TOOLS to /C:, then deleted it and recreated it as an extended partition ?

---

### Post by Quackers on 2011-07-13
Other people in your position have deleted the HP TOOLS partition then created an extended partition in the free space created by shrinking the C: drive.
The HP TOOLS partition contains some diagnostic tools, which I believe are downloadable from the HP site, if you ever need them (probably not).

---

### Post by oldfred on 2011-07-13
A few links in support of above comments:

The vendor recovery DVDs are just an image of your drive as purchased.  If you have housecleaned a lot of cruft normally included, run many  updates with many reboots, and added software you may want a full back  up.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by Veren on 2011-07-18
Thank you, I have done some research earlier, I just wanted to know some personal experiences. I am going to delete the RECOVERY and HP_TOOLS tomorrow and install Ubuntu, so wish me luck (:

---

### Post by Quackers on 2011-07-18
Don't forget to make a couple of copies of the recovery dvd's!

---

### Post by coldraven on 2011-07-18
My HP laptop had the same setup. I used Clonezilla to make backups then deleted the lot!
Windows now lives in VirtualBox where it belongs, in a box!

---

