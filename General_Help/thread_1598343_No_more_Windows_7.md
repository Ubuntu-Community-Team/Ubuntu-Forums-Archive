---
title: "No more Windows 7?"
date: 2010-10-16
forum: General Help
---

### Post by iBrigadier on 2010-10-16
Hey, thanks for reading.

I have a major problem with Windows 7's MBR. :confused: I deleted Ubuntu's partition last night, and when I restarted, I saw:
```
error: no such partition
grub rescue>
```I looked it up, put some code into a LiveCD terminal, and I thought it worked. But now, I says that I definitely need to put in a Windows 7 CD and do that MBR fix method. I did not own a Windows 7 CD; my laptop came with it pre-installed, and I have no recovery partition anymore. I'd appreciate any help, and thanks for reading.

---

### Post by psihokiller4 on 2010-10-16
what live cd and what code

EDIT: if you're lucky you'll just have to repair the MBR

---

### Post by Quackers on 2010-10-16
It would have been wise to make a set of recovery discs before deleting the recovery partition. If you google around there are sites that have recovery discs available for download.

---

### Post by inso_741 on 2010-10-16
If you install ubuntu again it will auto add windows to grub boot menu
If you dont want to install ubuntu you will probably have to get those recovery discs as Quackers said for that I'd suggest asking at windows forums

---

### Post by Hack.The.Pow. on 2010-10-16
try this [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

I believe that was what I used when the same thing happened to me

---

### Post by WorMzy on 2010-10-16
When you deleted Ubuntu's partition, you removed most of grub. Now grub is failing to load because it can't find it's files. There are two solutions, both of which are simple. You can either:
[LIST=1]
[*]Reinstall Ubuntu and grub, _**OR**_
[*]Install the Windows bootloader to the MBR
[/LIST]

You'll need a Windows disk for the second option. You can find instructions on how to use it to install the Windows bootloader on these forums on on google.

---

### Post by wilee-nilee on 2010-10-16
Here is a link to a recovery disc, and a set of commands just run the one bold command.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by iBrigadier on 2010-10-16
Thank you all very much for your replies! :) I have downloaded the .iso, but I'm trying to find out how to mount it to another USB (have no CDs). Ubuntu's kind of difficult for beginners.

EDIT:
I'd feel better if I waited until I am able to fully dedicate this laptop to Ubuntu. Had problems with dual-booting in the past as well.

---

### Post by dougalkerr on 2010-10-16
If your laptop is quite modern then you could install Ultimate Edition over the Ubuntu version you have. Delete the Linux partition and then assign it to Linux again using / as the Moint Point in the Linux partitioner. Remember of course that you need a Swap area just as Windows does. You should create a small partition when you are in the Partition manager and allocate twice the amount of RAM that you have installed for the Swap area, then choose to assign it as Swap under the file type. You won't need to assign a Mount Point as Linux will do this automatically for the swap file.

I find Ultimate Edition (available separately from Ubuntu - google it) is much more forgiving than plain Ubuntu and prettier too.
It can take a while to load but, once loaded it has heaps of programs already loaded and I have not had to load any codecs for anything on the Web. The odd occasion I have had to add Flash to a site but, three options for Flash are usually shown when this is asked for and I just add each in turn till the web page is happy to run the Flash video.

Any way I digress, Ultimate Edition or UE to us full time users is a very nice system to use and like the Ubuntu forum it has it's own forum with it's own experts.
I have always found them very helpful.

Give it a try, what do you have to lose? It will dual boot with Windows exactly the same way that Ubuntu does and you have the option when logging in to use either the Gnome desktop environment which is Ubuntu default or KDE (see panel at bottom of the Login screen once it appears).
Although KDE looks very neat it can take a little getting used but, none more so than Ubuntu.
The default Gnome environment is what I would advize you to try out. All you need should already be installed. Go on give it a go.

---

### Post by slooksterpsv on 2010-10-16
[http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

I recommend that as well, another person posted it above, that should work.

The others I'm disappointed in, put in your cd/dvd - well you clearly stated in your initial post that you don't have the DVDs/CDs. Try to be more careful people and read the post before you jump - otherwise, I would download Windows 7 from the internet cause technically you have a valid license and you're only requesting it for backup/restoration purposes and to do it that way.

---

### Post by crackpotfox on 2010-10-16
You do know that you get a windows CD/ DVD with ANY windows PC that you buy... Where did you get the computer?

---

### Post by iBrigadier on 2010-10-16
> **crackpotfox said:**
> You do know that you get a windows CD/ DVD with ANY windows PC that you buy... Where did you get the computer?

It's the eMachines e627 from Walmart's Black Friday 2009 sale. Messed up the recovery partition, and customer support told me I couldn't do anything about it.

Still looking into how to get that .iso running from boot. :confused:

---

### Post by Hukei on 2010-10-16
Easiest way to fix this, in my opinion, is using Hiren's Boot CD.

First, download it from here:
[http://www.hirensbootcd.net/download.html]("http://www.hirensbootcd.net/download.html")
(Just click on the "Direct HTTP Mirror" link below the Google AD)

and follow the instructions here to make it a bootable usb:
[http://www.hiren.info/pages/bootcd-on-usb-disk]("http://www.hiren.info/pages/bootcd-on-usb-disk")

After that, just boot the usb (make sure you set up your BIOS for this) and hit enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)".

Once you do that, if you want to repair the mbr, feel free to press F8 a couple of times exactly right after you press Enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)". If done correctly you should get your Windows 7 Menu for booting in Safe Mode and whatnot. Just press enter on "Computer Repair" (or something like that... is the only thing that has the word Repair on it). And then follow wilee-nilee's instructions if you want to get rid of grub and to fix the mbr.

PS: If you don't hit F8 fast enough after you press enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)", you'll simply boot into Windows 7.

By the way, Hiren's Boot CD is an AWESOME tool to have around in case you screw some stuff on your mbr. You can boot Windows 7/Vista/XP without having to fix it.

---

### Post by wilee-nilee on 2010-10-16
> **Hukei said:**
> Easiest way to fix this, in my opinion, is using Hiren's Boot CD.

First, download it from here:
[http://www.hirensbootcd.net/download.html]("http://www.hirensbootcd.net/download.html")
(Just click on the "Direct HTTP Mirror" link below the Google AD)

and follow the instructions here to make it a bootable usb:
[http://www.hiren.info/pages/bootcd-on-usb-disk]("http://www.hiren.info/pages/bootcd-on-usb-disk")

After that, just boot the usb (make sure you set up your BIOS for this) and hit enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)".

Once you do that, if you want to repair the mbr, feel free to press F8 a couple of times exactly right after you press Enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)". If done correctly you should get your Windows 7 Menu for booting in Safe Mode and whatnot. Just press enter on "Computer Repair" (or something like that... is the only thing that has the word Repair on it). And then follow wilee-nilee's instructions if you want to get rid of grub and to fix the mbr.

PS: If you don't hit F8 fast enough after you press enter on "Boot from Hard Drive - Windows Vista/7 (BOOTMGR)", you'll simply boot into Windows 7.

By the way, Hiren's Boot CD is an AWESOME tool to have around in case you screw some stuff on your mbr. You can boot Windows 7/Vista/XP without having to fix it.

Don't you love Hirens.;)

A super grub download on a thumb might get you to the command line in f8 as well. Might boot you right into   Windows. 

I have never been able to get that recovery ISO to boot from a USB, and I have various linux and other methods which will load a XP ISO.

---

### Post by iBrigadier on 2010-10-16
Followed that Hiren's Boot thing to the letter, and nothing works. :-(

Isn't there an Ubuntu program that can burn a bootable .iso to a SanDisk jumpdrive?

---

### Post by wilee-nilee on 2010-10-16
> **iBrigadier said:**
> Followed that Hiren's Boot thing to the letter, and nothing works. :-(

Isn't there an Ubuntu program that can burn a bootable .iso to a SanDisk jumpdrive?

So this computer has no cd reader, and or you don't have access to one is this correct?

---

### Post by iBrigadier on 2010-10-16
I do have a DVD/CD tray, the thing is, I just don't own a Windows 7 Home Prem DVD. Was hoping to be able to just drag and drop the .iso to the jumpdrive, but that's not going to be so easy with Ubuntu.

---

### Post by wilee-nilee on 2010-10-16
> **iBrigadier said:**
> I do have a DVD/CD tray, the thing is, I just don't own a Windows 7 Home Prem DVD. Was hoping to be able to just drag and drop the .iso to the jumpdrive, but that's not going to be so easy with Ubuntu.

Gosh a third party recovery ISO not being able to drag and drop and boot; with a USB, with totally different OS, do you see where I'm going.

Burn a cd of the ISO recovery link and run the command and get on with your life.;)

---

