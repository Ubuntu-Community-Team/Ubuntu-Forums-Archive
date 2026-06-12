---
title: "Broken Windows XP"
date: 2006-03-14
forum: General Help
---

### Post by micknisbet on 2006-03-14
Okay so I have a laptop with Windows XP installed.

I ran the Ubuntu installer, successfuly installed it to a new partition hoping to have a nice dual boot system.

Unfortunately Ubuntu loads nicely, but Windows XP wont load at all. It keeps telling me it cant read from the disk. I've tried repair installs, but it doesn't help. 

Can anyone help me? Do you need more info?

---

### Post by mavr on 2006-03-14
Yes, more info please. Have you messed around with the partitions? Does your linux see your windows partition if mounted?

---

### Post by micknisbet on 2006-03-14
I had to partition the drive in Ubuntu to install it on a new partition

My partition set up was

1 - Windows partition
2 - Ubuntu partition
5 - Ubuntu swap file

In my efforts of trying to get this to work I installed Ubuntu again, so now my partition table looks like this

1 - Windows partition
2 - Ubuntu partition
3 - Ubuntu partition
4 - Ubuntu swap file
5 - Ubuntu swap file

I cant see the Windows partition in Ubuntu, all I can see is 2 hard drives (hda1 & hda2), hda1 I cant see as it tells me I dont have permission.

When I try to boot into Windows XP, I get the following error message:

Booting 'Windows NT/2000/XP (Loader)'

root (hd0,0)
  filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

It seems to be stuck there....

---

### Post by dermotti on 2006-03-14
You could always put your windows XP cd in and boot into the recovery console

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

this will at least fx your windows XP....but you wont have linux anymore.

---

### Post by micknisbet on 2006-03-14
Thanks for the suggestion, but I've tried that and it doesn't fix windows, it just removes the ability to log in to Ubuntu also....

---

### Post by micknisbet on 2006-03-14
Okay, latest update is I've used the Windows XP setup disk to delete all partitions apart from the Windows XP one.

I've tried running a repair install of Windows XP, but when it gets to the stage of needing to restart and boot from the hard drive, it says it cant read from the disk. Do I need to somehow set this partition to be bootable again?

---

### Post by stabface on 2006-03-14
Yes, you need to have your windows be bootable drive on the disk, grub will figure it out with linux but windows will cry if it is not the first and bootable, that could have been your problem if you made the windows drive not bootflaged.

---

### Post by micknisbet on 2006-03-14
Okay, well how would I do that?

---

### Post by tyspot on 2006-03-14
in the recovery mode of the Win CD, use the fixboot or fixmbr commands. I think the Fixmbr is only on the OEM OPK cd. you could also give bootcfg a try to see if it details what has happened to your boot.ini file.

just one more question, this was not a raid configured IDE drives under windows were they?
Hope to Spot it wasnt.....

---

### Post by mavr on 2006-03-14
> filesystem type unknown, partition type 0x7

I am more scared u could have make something wrong the partition table when u  installed ubuntu. Did u change the filesystem or something like that? Or u told him to just load it as it is and make it bootable? That could explain also why u can't see your win from linux. By default it should be readable. I am afraid you made something wrong. I hope i am wrong and u can fix it.

---

### Post by drato on 2006-03-14
This is a fairly common type of problem, I have it whenever I install linux on a machine, and read about it on alot of threads

I'm no expert at manipulating grub and do not totally understand how this fix works out (more or less a hack, but windows will actually boot)
First: backup your grup file by typing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
into the terminal

this way you can restore your grub config file should something go wrong
next, pull up the grub config file:
```
sudo gedit /boot/grub/menu.lst
```

set your grub menu entry for windows (should be at the bottom of the file) to look something like this:

```
title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd1) (hd0)
savedefault
chainloader     +1
```

then save, reboot, and try windows

I can't tell you why this works or garuntee that it will (if anyone can explain it to me I'm quite curious) but for my setup it does, even though windows is my first hard drive (should be hd(0,0)

hope this helps!

---

### Post by micknisbet on 2006-03-15
Where do I type these commands?

When I edit the line inside grub to "root (hd1,0)" It wont boot telling me it cant find the hard drive.

I'm starting to fear that this has no resolution.

Also, I've tried fixboot and fixmbr a few times to no avail.

---

### Post by drato on 2006-03-15
Another thought I just had:

It sounds like grub doesn't like the partition type (ntfs and linux don't play together well in general)

Try changing your original config:

```
root (hd0,0)
savedefault
makeactive
chainloader +1
```

to: 

```
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

in the menu.lst file and see if it won't let you boot windows

---

### Post by micknisbet on 2006-03-16
Thanks for the suggestion, but it still cant read from the disk.

---

### Post by rolfkaese on 2006-03-21
I have the same problems since I updated the kernel today. I also mounted a new-partitioned FAT32 partition, but after i did a reboot, the win-xp boot line in GRUB was gone. I looked up my menu.lst and the entry for xp really was gone...
I added it again, rebooted and chose it in grub, getting this error:
Filesystem type unknown, partition type 0x82
Error 12: invalid device requested


and that sucks lol, i looked up my fstab and nothing looks wrong, heck even in ubuntu i looked partition information and it shows me it detects the partition as NTFS. :/

any suggestions on what to do? i can post my fstab and menu if that helps :/

---

### Post by drobvice on 2006-03-21
I'm new to linux and ubuntu but I just had an issue where I had windows on a disk and installed ubuntu to a second partiton on the same disk.  I thought I lost my whole window part.  But the problem was the default on the installer is to make ubuntu bootable.  I booted ubuntu and in teminal ran "sudo fdisk", typed "m" for options, then "a" and the /dev/hda or which ever drive.  That solved my problem but (assuming you can boot ubuntu now) not sure if it's the same as yours.  Also in the future, the lightning bolt is the default bootable drive.  Credit goes to Lunixfanboy for this info.  Hope it helps and sorry if I'm stating the obvious to anyone in thread.

---

### Post by rolfkaese on 2006-03-22
hmm.. that didnt help :/
I now tried to run the fixmbr via windows recovery CD, but now the partition where my win xp is installed too is missing... ;_; I can't access it from ubuntu nor recovery console from the cd... sh*t that's what you get for updating ubuntu <_<

Also I just noticed that in the boot sequence of Ubuntu it says "Local filesystem : failed" ... what does that mean? It's all very strange since it ran perfect before i did the updates yesterday... should I open a new thread for my problem?

---

### Post by drobvice on 2006-03-22
That sounds vaguely familiar.  I had the same problem when reinstalling some other distro (might have been mandrake or fedora core) a couple of years ago.  I messed up window totally.  At first I could see the windows partition from linux, then tried to fix it and lost it completely.  I ended up having to reformat it and reinstall.  Sucked badly.

---

