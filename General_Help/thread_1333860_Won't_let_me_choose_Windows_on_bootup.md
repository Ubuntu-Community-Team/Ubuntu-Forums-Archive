---
title: "Won't let me choose Windows on bootup"
date: 2009-11-21
forum: General Help
---

### Post by mondo45 on 2009-11-21
I have today installed Ubuntu.  The guide says that "After your PC has rebooted, Ubuntu will load (or give you the choice to start Windows if you also have that installed)."   However, when I do a cold boot, the menu option for operating system (black screen) lasts only 10 seconds or so, and the up/down arrows don't work, which means that I can't select Windows.  

For various reasons, I need to reboot in Windows.  It feels like Ubuntu has hijacked my 'puter.  What do I do to get a proper choice to boot Windows if I want??

Not a good start, I'm afraid.

---

### Post by mondo45 on 2009-11-21
Further information.  Have just rebuilt a new 'puter.  It has Windows XP on it.  I thought I would try Ubuntu, and purchased it with a Linux Special Edition magazine with a free DVD.  The DVD is LXFSDVD19.  

I went through resetting the partitions to make room for Ubuntu, and it loaded and booted fine.  Have been exploring the net with Firefox.  All good.  It prompted me to update to Ubuntu 9.10 which I have done.

The issue for me is that my techie (a son in IT support) pleaded with me not to load Linux.   Stay with Windows.  Obviously he is a Windows bloke.  I'm embarrassed, and I really want to sort it for myself. 

Looking at boot problems, I can see that it is to do with the Grub default, which I need to set to 4 (Windows) rather than 0.  My issue is how do I do that?   I am old enough to remember the old C: prompt days of DOS, and have put in instructions there many times.  Is that what I do here?  How do I get the C: prompt??  I know, newbie questions.  But please bear with me.  I would love to solve this one by myself.  

I can always wipe the hard disk and reload Windows, and give up on Linux.  But I do want to explore Linux.

---

### Post by meazz1 on 2009-11-21
Are you using a windows usb keyboard, change the KB or enable usb legacy support in BIOS.I had the same problem and turned out that the USB keyboard was the issue.

---

### Post by mondo45 on 2009-11-21
Meazz.  Thanks for your response.  Yes it is a MS USB keyboard.   Can you be a bit more explicit as to what I have to do, where, to fix it?   Thanks in advance.

---

### Post by darco on 2009-11-21
If you loaded Grub2, then try running this command in a terminal

```
sudo update-grub
```

good luck

darco

---

### Post by egalvan on 2009-11-21
> **mondo45 said:**
> Have just rebuilt a new 'puter.

A new computer should NOT have USB keyboard problems.

I have run many computers with USB keyboards, and NO boot problems.

I am not familiar with LXFSDVD19,
are you sure it is Ubuntu?

---

### Post by egalvan on 2009-11-21
> **mondo45 said:**
> 

The issue for me is that my techie (a son in IT support) pleaded with me not to load Linux.   Stay with Windows.  Obviously he is a Windows bloke. ** I'm embarrassed, **and I really want to sort it for myself. 
.

Embarrassed by what? Your son likes Microsoft,
and you want to learn something new.

Have at it :)

All of us here on these forums started out knowing nothing of Linux, at one time in the past.

Two years ago, I did not have a working install of Linux.
I now have close to 80 installs, running well.

---

### Post by mondo45 on 2009-11-21
It says Ubuntu on the DVD.  I should have given the extra detail in smaller letters under LXFSDVD19 it says LSFS19/07/09 Made in EU.

---

### Post by mondo45 on 2009-11-21
Well actually, I have never liked Microsoft or their software.  Far too expensive.  Monopolistic, but mainly klutzy, poorly designed fatware.  In particular, the menus are all very counterintuitive, but we have all learned the language now. 

I very much like the idea of Open Source and Linux.  In the past I used to use Quattro Pro, a far better spreadsheet than Excel, and also was a great fan of PC Outline in the DOS days.

---

### Post by darco on 2009-11-21
Did the command help or not?

---

### Post by mondo45 on 2009-11-21
Thanks for your response Darco.  However, can I confess that I find your guidance a bit too cryptic?  Do you mean that I should do a cold boot of the 'puter, and then do what exactly?  Before the boot routine takes over?  Please be gentle....

---

### Post by darco on 2009-11-21
ok, when you mentioned the old DOS days I assumed you knew about accessing a terminal.
Go to Applications/Accessories/Terminal
Enter the command, it may prompt for a password, so hopefully you have it. Then let the command run. It should detect your Win partition. Then just reboot.

darco

---

### Post by mondo45 on 2009-11-21
Thanks Darco.  It was a long time ago.  :)  And I was by no means a techie.  Will try what you suggest.

---

### Post by mondo45 on 2009-11-21
Sorry for being thick Darco.  But where do I enter Applications/Accessories/Terminal?  Presumably on teh System menu within Ubuntu somewhere?  Right?

---

### Post by mondo45 on 2009-11-21
Sorry Darco.  I WAS being thick.  I found the Terminal log in and have done what you suggest.  I am about to reboot to see what happens.  Thanks.

---

### Post by mondo45 on 2009-11-21
Did that.  And a cold reboot.  Only trouble is that it just sailed past the menu choice where I could have chosen windows again, after waiting (I think) 5 seconds!  Same as before.  

It does look like the keyboard is not responding in that environment.

---

### Post by darco on 2009-11-21
ok but you did see the option to choose the windows partition?

---

### Post by mondo45 on 2009-11-21
When I loaded in sudo update-grub (followed by my login password) it gave the following text:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

ray@ray-desktop:~$

---

### Post by mondo45 on 2009-11-21
Darco "ok but you did see the option to choose the windows partition?"

No.  I didn't see that choice.

---

### Post by mondo45 on 2009-11-21
After I put in the password, it just rattled through that routine that I copied above.

---

### Post by darco on 2009-11-21
ok, you dont have Grub2 installed. You have legacy Grub installed so the command would not work in this environment.
Try this link

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


good luck

darco

---

### Post by mondo45 on 2009-11-21
Thanks Darco.  Will see how I go.

---

### Post by 73ckn797 on 2009-11-21
Open up the terminal and enter:
```
sudo fdisk -l
```
Post the results. You will have to enter your password when prompted. Highlight the info with the mouse, right click and copy. Then paste in reply.

Also enter:
```
sudo blkid
```

Post results.

If you do not have a Windows installation you will not be able to boot.

Also, Which version of Ubuntu are you using?

---

### Post by darco on 2009-11-21
I may have posted the wrong link, but yes, run sudo fdisk -l.

---

### Post by mondo45 on 2009-11-21
Appreciate your help guys.  Currently running Ubuntu 9.10 having been prompted to update today.  I'm pretty sure that the distribution was 9.04.  

In the command prompt you suggested, was it sudo fdisk -l or sudo fdisk -1 (the first being letter l (ell) and the second being numeral 1)

---

### Post by mondo45 on 2009-11-21
ran sudo fdisk -l.  Here is what it gave:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cc43fdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47359   380411136    7  HPFS/NTFS
/dev/sda2           47360       60801   107972865    5  Extended
/dev/sda5           47360       60249   103538893+  83  Linux
/dev/sda6           60250       60801     4433908+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fde025e


Does that mean something to you guys?



   Device Boot      Start         End      Blocks   Id  System
ray@ray-desktop:~$ 

Also ran sudo blkid.  here is what it gave:

/dev/sda1: UUID="6E84971B8496E4BD" TYPE="ntfs" 
/dev/sda5: UUID="77eeb0f2-f48a-49e5-8647-697738835095" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="e51a4a85-fdda-44c5-b0a5-0bdef46de5e0" 
ray@ray-desktop:~$

---

### Post by mondo45 on 2009-11-21
When my IT guy built the 'puter yesterday, he installed Windows XP.  But not yet all the applications/files.  I adjusted the partitions to give 100 GB to Ubuntu leaving 400GB (or most of it anyhow) for Windows XP.

---

### Post by 73ckn797 on 2009-11-21
> **mondo45 said:**
> ran sudo fdisk -l.  Here is what it gave:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cc43fdd

   Device Boot      Start         End      Blocks   Id  System
** /dev/sda1   *           1       47359   380411136    7  HPFS/NTFS**
/dev/sda2           47360       60801   107972865    5  Extended
/dev/sda5           47360       60249   103538893+  83  Linux
/dev/sda6           60250       60801     4433908+  82  Linux swap / Solaris
Also ran sudo blkid.  here is what it gave:

** /dev/sda1: UUID="6E84971B8496E4BD" TYPE="ntfs" **
/dev/sda5: UUID="77eeb0f2-f48a-49e5-8647-697738835095" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="e51a4a85-fdda-44c5-b0a5-0bdef46de5e0" 
ray@ray-desktop:~$


Yes, I see Windows is there.

Good info here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

In the link you will find the following info: 
```
**Command line**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.
[/LIST]

```Follow these instruction and you should be able to rebuild the Grub Menu.

You can also go to:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

They have a disk you can burrn to do the restoration. Do the link above first.

There is info in the grub.lst file that will show a typical Windows grub boot listing.

In terminal enter:
```
 gksudo gedit /boot/grub/menu.lst
```Read through that and you will learn a lot of good info. ***Be careful that you do not change anything without knowing what you are doing.***  You can post the last section of the menu.lst and we can help you out. It is the section at the end that actually will list the boot menu options. Post that info in a reply.

Thia all assumes that you are not having any keyboard problem.

I run 9.10 so the "menu.lst" no longer applies.

---

### Post by mondo45 on 2009-11-21
Well.  Safely back in Windows.  I plugged in a PS2 Keyboard (as suggested by meazz!) and was able to select Windows in the boot routine.  Wheww.
 
I have to say it was a scary experience.  Not really up to solving command line problems with Grub files etc.  I formed the impression that Linux was user friendly these days, but ................
 
Anyhow, thanks for all of your help.  I still like the idea of Linux, and will be back - when I can pluck up the courage!

---

### Post by 73ckn797 on 2009-11-21
> **mondo45 said:**
> Well.  Safely back in Windows.  I plugged in a PS2 Keyboard (as suggested by meazz!) and was able to select Windows in the boot routine.  Wheww.
 
I have to say it was a scary experience.  Not really up to solving command line problems with Grub files etc.  I formed the impression that Linux was user friendly these days, but ................
 
Anyhow, thanks for all of your help.  I still like the idea of Linux, and will be back - when I can pluck up the courage!

I had to replace my keyboard this week. I had to use a USB to PS2 adapter. Windows had problems when I first booted into it but made the adjustment. I still will get the USB working.

---

### Post by egalvan on 2009-11-22
> **mondo45 said:**
> Well.  Safely back in Windows.  I plugged in a PS2 Keyboard (as suggested by meazz!) and was able to select Windows in the boot routine.  Wheww.

Again, no modern BIOS should have a problem with USB keyboard or mouse.

Next, once GRUB starts, the BIOS has completely finished it's function,
so any USB problem is not BIOS related.
GRUB is a mini operating system in its own right, with I/O drivers built in. It's been able to figure out USB for ages.


> 
I have to say it was a scary experience. 
 Not really up to solving command line problems with Grub files etc.
  I formed the impression that Linux was user friendly these days, but ................
 
Athanks for all of your help.  I still like the idea of Linux, and will be back - when I can pluck up the courage!

If you are not comfortable using the command line to edit the menu.lst,
then use StartUpManager, a GUI-based front-end that will allow you to manage many boot-time parameters.

It will be under the System>Administration menu.
and it's call StartUp-Manager.
if it's not there, then install it,
with Synaptic, search for *startupmanager*

I use command line often, but find StartUpManager a little easier to work with on some options, particularly grub-boot screen resolutions.

The author of StartUpManager is reported to be hard at work on the new version that will support GRUB2.

---

