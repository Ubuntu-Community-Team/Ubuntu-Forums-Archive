---
title: "boot.ini"
date: 2010-02-22
forum: General Help
---

### Post by zonedabone on 2010-02-22
Hey, there. I installed ubuntu using a disk image, and now, when I boot, it just goes directly to ubuntu, which is corrupted. I'm running ubuntu from the disk right now, and I want to change my boot.ini file so that it just points to windows xp. How can I do this from within ubuntu? I've tried using the windows setup disk, but none of my admin passwords work. Thanks in advance!:D

---

### Post by hithisisatempaccount1532 on 2010-02-22
I'm no expert but I don't think boot.ini has anything to do with what OS starts first unless you're booting off an external or removable drive storage...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have the windows recovery disk you can go into it and do fdisk /fixmbr which should rebuild the MBR overwriting the GRUB config but will disable Ubuntu I think... 

Once again I'm no expert and am just giving my rough understanding of the situation.
I think that dual booting with windows installed first is a pain to have them work together.

---

### Post by zonedabone on 2010-02-22
I've got that problem where none of my password work, but my only windows disk is sp1 from 2002, and so it doesn't have the fix. It there any other software that can modify the mbr?

---

### Post by hithisisatempaccount1532 on 2010-02-22
Fortunately since you said you had your Ubuntu CD still there you can try to reinstall it and have it co-exist with the Windows partition if it is on your PC - that's the only other solution I can think of without losing the Windows partition.

And I wish someone would answer my questions in my thread. ;'(

---

### Post by zonedabone on 2010-02-22
Well, here I am to ruin your day! My main disk is full, so ubuntu won't install to it! Next, please! :D

---

### Post by hithisisatempaccount1532 on 2010-02-22
Hmmmm... Next I suppose you could manually go through the MBR settings using the terminal in the LiveCD... that will take a few steps though.

---

### Post by zeroseven0183 on 2010-02-22
What version of Ubuntu did you install? And how did you install it?

If you installed Ubuntu 9.10, you have the default GRUB2 (boot loader  and boot  manager). And the way to access the list is by holding SHIFT during boot. See if you can do this and select Windows XP. Once  you're in Windows, then you can modify your boot.ini.

If you installed Ubuntu inside Windows, try to look for the folder /host, and see if you find the boot.ini file from the Windows root directory.

What's wrong with your Ubuntu that you said it's corrupted?

---

### Post by hithisisatempaccount1532 on 2010-02-22
Listen to zeroseven0183, he knows what he is doing... I don't..

---

### Post by zeroseven0183 on 2010-02-22
Hmmm... Before doing something else, can I remind you to backup your data first if you haven't done that?

This way, if everything goes wrong, you're sure the files are secured.

---

### Post by zeroseven0183 on 2010-02-22
> **hithisisatempaccount1532 said:**
> Listen to zeroseven0183, he knows what he is doing... I don't..

Flattering. Need to straight things up first so I'm still probing with questions.
Yes, you can also. Let's do this both and hope someone who's better will also join.

---

### Post by zonedabone on 2010-02-23
All backed up! I'm going to shut off now. Going into battle! Wish me luck!:D

---

### Post by zonedabone on 2010-02-23
I held down shift while starting up, but It still just tried to start. By the way, if this helps, I get this whenever I try to start:

```
Starting GRUB.
Error: Disk doesn't exist
GRUB rescue> _
```

---

### Post by zonedabone on 2010-02-23
[PHP]def bump:
      print "BUMP!"
      global.bump = true[/PHP]

Haha!

---

### Post by harrisonk on 2010-02-23
[SIZE=2]Does it load any splash menus?

From what I see you don't have GRUB2 Installed look here:[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
It's near the bottom so you will have to scroll down.

Harrisonk
[/SIZE]

---

### Post by zonedabone on 2010-02-23
Actually, I think I know what to do! I just need to know what commands in the liveCD terminal can be used to edit the MBR. And help appreciated!:D

---

### Post by zeroseven0183 on 2010-02-23
Here's how to recover your MBR with the LiveCD [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

### Post by zonedabone on 2010-02-23
Great! Going back to the battlefield! Wish me luck!:D

---

### Post by zonedabone on 2010-02-23
I got an error with the command in the terminal. The kernel "sudo" couldn't be found. What should I replace sudo with?

---

### Post by harrisonk on 2010-02-23
[SIZE=2]Sounds like you need a new cd.[/SIZE]

---

### Post by zonedabone on 2010-02-24
Actually, I wasn't using the right terminal. :)
Now I'm in the REAL terminal, and I get this:

```
ubuntu@ubuntu:~$ sudo apt-get install ms-sys 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

```

I want it booting to drive C! Should I disconnect E, or is there some other way?

---

### Post by zeroseven0183 on 2010-02-24
I see. Sorry but I think the HowTo is obsolete and the package is no longer in the repositories.
I found ms-sys in [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/). The instructions are also in that site.

You can also try the Hiren's BootCD [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/). It has lots of tools/utilities to fix things.
Download the ISO and burn it to a CD.

---

### Post by Mark Phelps on 2010-02-24
> **zonedabone said:**
> Hey, there. I installed ubuntu using a disk image, and now, when I boot, it just goes directly to ubuntu, which is corrupted. I'm running ubuntu from the disk right now, and I want to change my boot.ini file so that it just points to windows xp. How can I do this from within ubuntu? I've tried using the windows setup disk, but none of my admin passwords work. Thanks in advance!:D

When Ubuntu is installed using Wubi in a system that has Windows XP, it adds an entry to the boot.ini file for selecting Ubuntu.

You should be able to do the following:
1) Boot from an Ubuntu LiveCD
2) Mount the partition containing XP
3) Use Gedit to edit the boot.ini file to remove the Ubuntu line (and only that line)
4) Save the edited file
5) Reboot the PC

After that, there will be no menu presented and the machine will boot into XP directly.

---

### Post by zonedabone on 2010-02-24
Hoho! I'm back! Running WINDOWS Firefox! 
I looked at the article, and someone had this terminal code:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR=Red]sda[/COLOR]
```Worked magic! Rebooted, and I had my options back! Thank you to everyone who helped! I'll just reinstall ubuntu using wubi. I worked for me before I installed those updates. 

Again, thanks to everyone that helped me with the problem!

:D:D:D

Zonedabone

By the way, I spilled the beans!

---

