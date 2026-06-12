---
title: "I need to uninstall and I do not have Vista CD!!"
date: 2009-08-15
forum: General Help
---

### Post by wizzle on 2009-08-15
Hello.
I am a Linux noob and I really like it but I need to uninstall it as the computer I used to test Linux is not mine. :P
I don't know how to uninstall this safely without the Vista CD and I can really use some help.

Thank you for your time,
Will

---

### Post by Vunutus on 2009-08-15
Well this is probably something you should have thought about beforehand. Operating systems aren't the kind of thing you can just "uninstall" like a program. If you want to play with Linux and not change the computer it's on you should use the Live CD instead of outright installing it to the hard drive (which sounds like what you did). It really depends on how you installed Ubuntu. Did you dual boot it with vista or did you tell Ubuntu to take the whole hard drive? If you had it take the whole hard drive than Vista and all original data is likely gone.

If you are intending to re-install Vista, there really isn't any way to do it without the original discs, short of pirating it (which I won't provide instructions for of course :D)

---

### Post by wizzle on 2009-08-15
> **Vunutus said:**
> Well this is probably something you should have thought about beforehand. Operating systems aren't the kind of thing you can just "uninstall" like a program. If you want to play with Linux and not change the computer it's on you should use the Live CD instead of outright installing it to the hard drive (which sounds like what you did). It really depends on how you installed Ubuntu. Did you dual boot it with vista or did you tell Ubuntu to take the whole hard drive? If you had it take the whole hard drive than Vista and all original data is likely gone.

If you are intending to re-install Vista, there really isn't any way to do it without the original discs, short of pirating it (which I won't provide instructions for of course :D)
It is a dual boot. I still have windows on my machine; both windows and ubuntu  run well. Is there anyway I can safely remove ubuntu without risking my vista files? Thank you for your response.

---

### Post by wizzle on 2009-08-15
If this is not possible, I would like to know if I can repartition the amount of space used in the "/" directory in ubuntu, because as of right now I cannot perform any updates in ubuntu because it says I have insufficient space but I still have approximately 60GB free space on my hard drive that I know of. Says I only have 70MB in the "/" directory I need to increase it to install updates and such..

---

### Post by sideaway on 2009-08-15
Hi there, you probably have a live CD. If so, you can use Gparted to wipe your ubuntu partition, make a new (small) partition and install GRUB on it. This will allow you to use grub to boot to windows. (since you can't reinstall ntbootmgr)

If you want to make / bigger, you can also use Gparted to extend, shorten and move partitions.

Hope this helps!

---

### Post by Megaptera on 2009-08-15
Here's a guide to re-sizing your vista partition, but as you've not got vista discs do **not** use it -why? 'Cos of what it says at the start:
"First make sure that you have a bootable Windows Vista installation DVD, as you will be unable to use your computer if you don&#8217;t."

Source of that instruction: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

As to the rest of your problem, merely removing Ubuntu won't solve the issue as you've made a radical change to the Maste Boot Record (MBR).

To try to help you I googled around 'repair vista mbr with no discs' and I couldn't find an answer. Do you want to try googling around with variations of that?

---

### Post by wizzle on 2009-08-15
> **sideaway said:**
> Hi there, you probably have a live CD. If so, you can use Gparted to wipe your ubuntu partition, make a new (small) partition and install GRUB on it. This will allow you to use grub to boot to windows. (since you can't reinstall ntbootmgr)

If you want to make / bigger, you can also use Gparted to extend , shorten and move partitions.

Hope this helps!
it wont let me download this. It says error I must manually install it in terminal and I try that too and it also fails. Ubuntu is ******* now :( am I screwed?

---

### Post by fluffman86 on 2009-08-15
If you used the graphical / Live-CD to install, then boot into that like you did before.  Once there, go to System > Administration > Partition Editor

This will allow you to edit your paritions.  First, you'll want to resize your Windows partition to make it smaller, then resize the Ubuntu partition to make it bigger.  This will take a VERY long time, and I recommend defragmenting Windows before starting this process.

That will let you make Ubuntu bigger, but if you still want to remove it then you'll need a way to restore the Master Boot Record for Windows.  One way to do this would be to borrow a Vista CD, boot to a recovery console, and type fixmbr (at least that's what you did with XP.)  You may also be able to restore the MBR with [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/) but I'll leave that as an excersize to the user to figure out.

Once you have Windows booting automatically with no option for Ubuntu, then you can once again use the Ubuntu live CD, but this time instead of resizing first, just delete the Ubuntu partition and then resize the Windows partiton to make it larger.

Edit: wow, you guys are fast typers!

---

### Post by wizzle on 2009-08-15
> **Megaptera said:**
> Here's a guide to re-sizing your vista partition, but as you've not got vista discs do **not** use it -why? 'Cos of what it says at the start:
"First make sure that you have a bootable Windows Vista installation DVD, as you will be unable to use your computer if you don’t."

Source of that instruction: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

As to the rest of your problem, merely removing Ubuntu won't solve the issue as you've made a radical change to the Maste Boot Record (MBR).

To try to help you I googled around 'repair vista mbr with no discs' and I couldn't find an answer. Do you want to try googling around with variations of that?
thanks for your efforts. I really got myself into a pickle here. Im trying all I can to solve this problem

---

### Post by wizzle on 2009-08-15
what is "live-CD"? I have a burnt copy of ubuntu that I used for the install that is all

---

### Post by Mardoct909 on 2009-08-15
The ubuntu install disk works as a live DVD. Choose the default option when you boot from the ubuntu disk to use it as a live DVD, then change your partitions with the partition editor as stated above.

---

### Post by lisati on 2009-08-15
> **wizzle said:**
> Hello.
I am a Linux noob and I really like it but I need to uninstall it as the computer I used to test Linux is not mine. :P
I don't know how to uninstall this safely without the Vista CD and I can really use some help.

Thank you for your time,
Will


Suggestion: Look for a recovery partition on the computer. On some computers you can press a special key at system start-up to initiate system recovery - my Compaq desktop uses F10, and my current Toshiba laptop uses the 0 (number zero) key.

As Vunutus and others indicated, it's unwise to install a new operating system without legal copies of the original OS's installation or recovery disks being available: as much as we hate to admit it, things can sometimes go wrong.

---

### Post by wizzle on 2009-08-15
I will try these ideas and will get back to you. I realize now how idiotic the decision was without the vista backup. Is there anyway I can obtain one without purchasing another copy of vista?

---

### Post by sideaway on 2009-08-15
Ubuntu comes as a live CD. So that CD you used, is a live one. Meaning you can boot to it. F12 or something similar at bios screen will allow you to select the boot device, insert the CD, and choose CD/DVD and the menu.

This will present you with an Ubuntu menu. You want the top most entry, this will load you with a 'live' ubuntu desktop running off the CD. You can then use Gparted to edit your partitions. To be honest I don't recommend you decrease the size of the Vista partition. This will in all likely kill windows, and then you'll NEED a Windows DVD. I suggest you remove some programs or irrelevant/obsolete packages/files or something similar to gain sapce. Playing with partitions I do not recommend. To remove Ubuntu, you could just reformat the Ubuntu partition and then use GRUB to boot to windows.

---

### Post by lisati on 2009-08-15
> **lisati said:**
> Suggestion: Look for a recovery partition on the computer. On some computers you can press a special key at system start-up to initiate system recovery - my Compaq desktop uses F10, and my current Toshiba laptop uses the 0 (number zero) key.

[U]
Afterthought[/U]: if Vista is bootable, you *might* be able to create a recovery CD/DVD: my laptop came with software preinstalled that let me do so quickly and easily.

---

### Post by wizzle on 2009-08-15
> **sideaway said:**
> Ubuntu comes as a live CD. So that CD you used, is a live one. Meaning you can boot to it. F12 or something similar at bios screen will allow you to select the boot device, insert the CD, and choose CD/DVD and the menu.

This will present you with an Ubuntu menu. You want the top most entry, this will load you with a 'live' ubuntu desktop running off the CD. You can then use Gparted to edit your partitions. To be honest I don't recommend you decrease the size of the Vista partition. This will in all likely kill windows, and then you'll NEED a Windows DVD. I suggest you remove some programs or irrelevant/obsolete packages/files or something similar to gain sapce. Playing with partitions I do not recommend. To remove Ubuntu, you could just reformat the Ubuntu partition and then use GRUB to boot to windows.
This is where I am at and I am clueless.
[[IMG]http://img149.imageshack.us/img149/9813/screenshotmvc.th.png[/IMG]]("http://img149.imageshack.us/i/screenshotmvc.png/")
Can anyone tell me the wisest choice to make from this step

---

### Post by fluffman86 on 2009-08-15
> **wizzle said:**
> I will try these ideas and will get back to you. I realize now how idiotic the decision was without the vista backup. Is there anyway I can obtain one without purchasing another copy of vista?

See the end of my post above.  [http://ubcd.sf.net](http://ubcd.sf.net) probably has a way to fix the MBR on Vista.  Then you can use the Ubuntu Live CD to delete Ubuntu, per the posts above.

> **sideaway said:**
> To be honest I don't recommend you decrease the size of the Vista partition. This will in all likely kill windows, and then you'll NEED a Windows DVD.

Standard precautions of backing up data always apply, but I'd like to say that I've resized my XP partition *AT LEAST* a dozen times with no errors.

---

### Post by Megaptera on 2009-08-15
That's the 'live cd'. Too late now but you could just have tried Ubuntu from that without installing. Runs slow but that's the only difference.

---

### Post by fluffman86 on 2009-08-15
> **wizzle said:**
> This is where I am at and I am clueless.
[[IMG]http://img149.imageshack.us/img149/9813/screenshotmvc.th.png[/IMG]]("http://img149.imageshack.us/i/screenshotmvc.png/")
Can anyone tell me the wisest choice to make from this step

Hey, you have a recovery partition.  Reboot into your Windows recovery partition and that usually acts just like a Windows CD.  

Look for "Recovery Console" there, and when you get to a command prompt type "fixmbr" (without the quotes).  Then follow my post on page 1.

---

### Post by sideaway on 2009-08-15
Vista appears to be less forgiving when resizing. I'd proceed with caution. I've killed an install when resizing. Only had to reinstall nt boot manager though.

Yes, just use the recovery partition and follow fluffmans instructions, that will erase GRUB though. But you can erase the Ubuntu partition in Windows.

---

### Post by wizzle on 2009-08-15
> **fluffman86 said:**
> Hey, you have a recovery partition.  Reboot into your Windows recovery partition and that usually acts just like a Windows CD.  

Look for "Recovery Console" there, and when you get to a command prompt type "fixmbr" (without the quotes).  Then follow my post on page 1.
I will try that it just a second. I found a vista backup CD I made when I 1st got my laptop.
[[IMG]http://img5.imageshack.us/img5/739/35475569.th.jpg[/IMG]](http://img5.imageshack.us/i/35475569.jpg/)
does this look like it will be a quicker, more straight forward fix?

---

### Post by wizzle on 2009-08-15
what if I boot into windows recovery partition and just boot windows back to factory default. Will that work (Ill back up all my files now). System Restore?

---

### Post by egalvan on 2009-08-15
you may be able to run a "fix windows" option, if you can boot into a recovery partition...


Using superGRUB, you may be able to recover your MBR without reloading.

[www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by Krupski on 2009-08-15
> **wizzle said:**
> It is a dual boot. I still have windows on my machine; both windows and ubuntu  run well. Is there anyway I can safely remove ubuntu without risking my vista files? Thank you for your response.

If the computer first had Windows, then later you installed Ubuntu, chances are that you installed GRUB (the Linux boot loader) to the master boot record of the primary hard drive.

Therefore, the computer now boots like this:

START
GOTO LINUX PARTITION
DISPLAY MENU
BOOT UBUNTU?
YES, BOOT UBUNTU
BOOT WINDOWS?
YES, LOAD AND BOOT WINDOWS


You see that the process now jumps to the UBUNTU partition first. This is all fine... but if you remove Ubuntu, the boot process will jump to... nowhere.

To fix this, you have to get the original Vista DVD, then boot up into "Repair this installation using the recovery console" mode, then type two commands:

```

FIXBOOT
FIXMBR

```

These two commands put the boot process back to normal... that is, Windows just boots itself. It no longer jumps to the Ubuntu partition first.

So, unless you can get a Vista DVD and repair the master boot record, you CANNOT delete Ubuntu or else NOTHING will boot up.

If you need any of this explained further, please feel free to ask.

-- Roger

---

### Post by wizzle on 2009-08-15
> **Krupski said:**
> If the computer first had Windows, then later you installed Ubuntu, chances are that you installed GRUB (the Linux boot loader) to the master boot record of the primary hard drive.

Therefore, the computer now boots like this:

START
GOTO LINUX PARTITION
DISPLAY MENU
BOOT UBUNTU?
YES, BOOT UBUNTU
BOOT WINDOWS?
YES, LOAD AND BOOT WINDOWS


You see that the process now jumps to the UBUNTU partition first. This is all fine... but if you remove Ubuntu, the boot process will jump to... nowhere.

To fix this, you have to get the original Vista DVD, then boot up into "Repair this installation using the recovery console" mode, then type two commands:

```

FIXBOOT
FIXMBR

```These two commands put the boot process back to normal... that is, Windows just boots itself. It no longer jumps to the Ubuntu partition first.

So, unless you can get a Vista DVD and repair the master boot record, you CANNOT delete Ubuntu or else NOTHING will boot up.

If you need any of this explained further, please feel free to ask.

-- Roger
thank you very much for your clear explanation. Will a friends copy of windows work on my PC for this operation?

---

### Post by wizzle on 2009-08-15
bump

---

### Post by wizzle on 2009-08-15
I have created a 5GB unallocated partition in Windows Vista. Now I have booted from Ubuntu CD and am looking to expand the partition so I can have room to install updates and such on Ububtu. How do I go about this safely from where I am now? 
----->[[IMG]http://img208.imageshack.us/img208/4615/screenshotkhc.th.png[/IMG]](http://img208.imageshack.us/i/screenshotkhc.png/)

---

### Post by wizzle on 2009-08-17
An answer would be highly appreciated, thank you.

---

### Post by BinaryFeast on 2009-08-17
> **wizzle said:**
> I have created a 5GB unallocated partition in Windows Vista. Now I have booted from Ubuntu CD and am looking to expand the partition so I can have room to install updates and such on Ububtu. How do I go about this safely from where I am now? 
----->[[IMG]http://img208.imageshack.us/img208/4615/screenshotkhc.th.png[/IMG]]("http://img208.imageshack.us/i/screenshotkhc.png/")

First: To all those who need to repair Vista, but who do not own a installation disc: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) (completely legal). It is the repair part of the install disc. Boot up the cd and restore the MBR. Then boot Vista and delete the Ubuntu partition in the partition manager.

About the resize:I would advise against using GParted for this. Use the disc management tool in Vista to shrink the Vista Partition (if it won't let you shrink it, despite obviously having free space, then follow this guide: [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)). The thing is that you may have important system files at the end of the Windows partition. Shrinking it with GParted will delete these and may cause all sorts of trouble.

---

### Post by wizzle on 2009-08-17
i have already gone into vista and deleted a 5gb partition as you can see in my image. Im just curious as to how I go about extending the ubuntu partition so I can actually update linux without getting an error saying I need to space in my "/" directory.

---

