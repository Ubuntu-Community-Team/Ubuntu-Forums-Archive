---
title: "Restoring GRUB After Windows Install"
date: 2006-03-16
forum: General Help
---

### Post by Symok on 2006-03-16
A few days ago I installed Ubuntu. It went really well, no problems with any drivers so far (Sound, NIC, etc). I also reinstalled Windows (realizing right after I should have reinstalled Windows FIRST:???: ) so I lost GRUB and can't access Ubuntu any more.

I've tried both the "Restore with install CD" and "Super GRUB Disk" methods from [this](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29) Wiki entry. The Install CD gave me an error "The file /boot/grub/stage1 not read correctly", and the Super GRUB disk just plain didn't work (using auto config).

I also tried following the guide in [this](http://ubuntuforums.org/showthread.php?t=76652) thread, but when I get to selecting the partition, none are listed for the drive that Windows/Linux is on (I posted a reply in there about it, but since its dropped to the second page now, I figured I probably wouldn't get a response there)

Another interesting thing is that Windows seems to be detecting extra paritions on my hard drive. Adding the sizes up in Windows drive management thing, the total is 29GB, the drive is only 20GB. Checking fdisk -l in Linux (from getting the rescue console) shows all the drives, with no gaps between beginings and endings.

Thanks for any help you can offer :)

---

### Post by Zelut on 2006-03-16
I also learned the hard way to re-install windows first, and Ubuntu later :)

I just restored grub this morning on my machine after re-installing windows last nite.  I used the following:

[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

Basically, boot from install CD using 'rescue'.  When you're given a prompt do 'grub-install /dev/hda'.

After doing that (despite errors I recieved) I did a reboot & everything was back to normal.

---

### Post by Symok on 2006-03-16
That's basically the same as what the Wiki entry says, I've tried it a number of times but it doesn't want to work...

---

### Post by Zelut on 2006-03-16
can you post the output of your 'fdisk -l'?  Maybe between the wiki & your installation we're getting the /dev in the wrong place.  Thanks

---

### Post by Symok on 2006-03-16
I made a mistake, I coulnd't get it from the recovery console (That gives me an error "cannot open /proc/partitions") But I was able to get it by starting the install and then going to a shell.

When I try the recovery console method, I mount /dev/HDA2 as the root file system (ls-ing shows the proper files, etc) but when I try grub-install /dev/hda2 (or /dev/hda, etc) I get the error mentioned in my first post

Here's my partition scheme acording to fdisk -l

```

Device  Boot Start  End    Blocks    ID   System
HDA1    *    1      608    4883728+  7    HPFS/NTFS
HDA2         609    1160   4433940   83   Linux
HDA3         1161   2491   10691275+ f    W95 Ext'd (LBA)
HDA4         1190   1320   1052226   b    W95 FAT32
HDA5         1161   1189   232879+   82   Linux Swap / Solaris
HDA6         1321   1418   787153    7    HPFS/NTFS
HDA7         1419   2363   7590618   7    HPFS/NTFS
HDA8         2364   2491   1028128+  7    HPFS/NTFS

```

Here's Windows' idea of my partition table:
[[IMG]http://img481.imageshack.us/img481/9537/parts7ty.th.jpg[/IMG]](http://img481.imageshack.us/my.php?image=parts7ty.jpg)
Thumbnailed because the full size one breaks the table

---

### Post by Symok on 2006-03-19
I really don't like bumping my own thread, but is there anyone else who has any ideas about this?

I also installed Partition Magic to see if I could at least set my linux partition to be the boot one through that, then try to get the boot loader working from the linux side, but it detected errors in my MBR, which it isn't able to fix (even though it says it can) then when it loads it just shows the hard drive as having an error. Trying to fix the MBR from the Windows recovery console also had no effect.

Thanks.

---

### Post by jerrykenny on 2006-03-20
kuyaedz's solution usually works fine, and is a shortcut to the solution on the first thread you followed . . . 

What error message do you get when you issue the command 

grub-install /dev/hda 

I dont see it on your thread . . . . .

---

### Post by red_shrike on 2006-03-20
Your problem is actually easy. All you had to do is start the Ubuntu installation again, and than when it gets you to the menu with all the steps, simply choose GRUB setup. Or whatever it says there for GRUB installing. This is the main advantage of Debianoids, ona may skip the install steps.

---

### Post by red_shrike on 2006-03-20
Dude! That free and unallocated space is unformatted space! If you format it, let's say in FAT32, you can use it. This is 10 GB of space wasted. You cn also try making special pertition for /home That way you can always chang distributions without fear from losing personal data.

---

### Post by Symok on 2006-03-20
[QUOTE=jerrykenny]kuyaedz's solution usually works fine, and is a shortcut to the solution on the first thread you followed . . . 

What error message do you get when you issue the command 

grub-install /dev/hda 

I dont see it on your thread . . . . .[/QUOTE]

The error message is:
"The file /boot/grub/stage1 not read correctly"

[QUOTE=red_shrike]Your problem is actually easy. All you had to do is start the Ubuntu installation again, and than when it gets you to the menu with all the steps, simply choose GRUB setup. Or whatever it says there for GRUB installing. This is the main advantage of Debianoids, ona may skip the install steps.[/QUOTE]

When I try to go through the install process again I get to the part of partitioning the hard drives, but none of the partitions for my system drive are displayed. When I "Go back" and try to select "install grub" it just takes me to the partition menu again.

[QUOTE=red_shrike]Dude! That free and unallocated space is unformatted space! If you format it, let's say in FAT32, you can use it. This is 10 GB of space wasted. You cn also try making special pertition for /home That way you can always chang distributions without fear from losing personal data.[/QUOTE]

No, those two partitons shouldn't exist. Its a 20GB hard drive, all of which is allocated to the partitions displayed in the posted output from the fdisk -l command in Linux.

---

### Post by red_shrike on 2006-03-21
Damn. Thats some weird stuff. I guess you might format the whole hard drive :rolleyes:

---

### Post by sYs^ on 2006-03-21
Hi!

I have exactly the same problem :\

I'm thinking about to boot my linux with the windows boot manager:

System Properties ->  Advanced -> Startup and recovery -> Settings -> and there Edit, what should I write there to boot linux? :D

My Ubuntu is on the 2nd disk's 3rd partition. something like this?

multi(0)disk(2)rdisk(0)partition(3)\boot="Ubuntu" 

is it possible?

Regards, sYs^


Edit:hmm, interesting: [http://www.tprthai.net/bootmgr.htm](http://www.tprthai.net/bootmgr.htm)
[http://www.highlandsun.com/hyc/linuxboot.html](http://www.highlandsun.com/hyc/linuxboot.html)

---

### Post by sYs^ on 2006-03-21
Problem resolved with GRUB.

Booted with live-cd, mount /dev/hdc2 /tmp/randomcucc , chroot /tmp/randomcucc grub started, entered: setup(hd0) , quit , reboot , boot with GRUB, had to edit manualy the GRUB menu (becouse it didn't find my linux on that partition), had to change (hd2,2) to (hd2,1) and ```
kernel          /boot/vmlinuz-2.6.15.6 root=/dev/hdc3 ro quiet splash
``` to ```
kernel          /boot/vmlinuz-2.6.15.6 root=/dev/hdc2 ro quiet splash
```

after this my ubuntu started, then I had to edit /etc/fstab and now it's working :>

Windows messed up my partitions...

sorry for this chaotic post , I got tired in this shit, but at least it's working finally :p

I hope it'll help

---

### Post by dotdot on 2006-03-27
hey folks - i have the same problem (pointed here from..
[http://ubuntuforums.org/showthread.php?t=151016](http://ubuntuforums.org/showthread.php?t=151016))

I've booted up live.

mounted /
mounted c/
mounted another win fs - df - tells me where everything is.

I've modded menu.lst
modded fstab

reboot - voila - the problem .. is still there.

..Any help would be much apprec -- I've got a dead lappie here :<

---

