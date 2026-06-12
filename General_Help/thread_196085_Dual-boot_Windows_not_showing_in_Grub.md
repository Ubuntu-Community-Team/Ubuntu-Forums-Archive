---
title: "Dual-boot: Windows not showing in Grub?"
date: 2006-06-13
forum: General Help
---

### Post by binjured on 2006-06-13
Okay, here's the story:

I have two harddrives.  The master has Ubuntu on it.  The slave has Windows XP on it.   When I went to install XP it complained that it couldn't write to the MBR of the master drive, it needed a partition or something.  Since I didn't have any space to let it do that I came up the bright idea of simply disconnecting the Ubuntu drive, putting the windows on SATA1, and installing Windows!  Okay, all went well, except now Ubuntu's Grub loader doesn't know Windows is there.  What file do I edit and with what to tell Grub to let the red-headed step child play too? :-$

---

### Post by zxee on 2006-06-13
The file that needs editing is /boot/grub/menu.lst
You can edit it by typing sudo gedit /boot/grub/menu.lst
I don't know what your windows partition is except that you say it's a sata drive now.
The lines to be entered in gedit are: title windows xp (next line) rootnoverify (hd?,?) *replace the question marks with the actual drive and partition numbers windows xp is on, remembering that grub starts counting from 0. (last line) chainloader +1
That should do it-hope that helps.

---

### Post by binjured on 2006-06-13
I tried that and it didn't work, I used (hd1,0) (it is my slave drive, C:\ is the only partition).   It simply sat at the loader and hangs with a blinking cursor.  I thought "hey, maybe it's a problem with XP since I didn't ever really finish that install (didn't go through first boot)" so I reinstalled Windows... booted fine.  I then switched the hds back around, and now Ubuntu nor Windows will load (hangs with blinking cursor) -- to get into Ubuntu I have to use the boot disk and select "boot from first hard disk".

Edit:  I got the whole "can't boot w/o disk" thing fixed -- my BIOS decided to put my external drive at the top of the HDD boot list.  However, the grub issue still remains.

What the hell have I done?

---

### Post by caldevil on 2006-06-13
So now I assume you can boot into ubuntu. See if you can mount the windows partition from there.

---

### Post by binjured on 2006-06-13
[QUOTE=caldevil]So now I assume you can boot into ubuntu. See if you can mount the windows partition from there.[/QUOTE]
Okay, I don't actually care about mounting it, but this is what I tried:

System->Administation->Disks
Selected HDD and partition -> Browse
the folder is empty, Properties says "Contents: unreadable", but it is showing up.  Free space also indicates that something around 3gb is installed (Windows) and partition type is NTFS.

Edit2:  using "sudo nautilus /tmp/disks-conf-sdb1" show files.

---

### Post by scxtt on 2006-06-13
if you can still reinstall them both w/o worrying about losing any data, i recommend this:

1. connect the disks to your mb however you want to leave them
2. partition the windows disk and install windows on the formatted/partioned master drive (SATA or IDE?)
3. install ubuntu wherever you want

while installing ubuntu, when it gets to the point where it installs grub, it should recognize your windows disk/partition and inform you of its existance before installing grub (most likely overtop of windows' MBR) ...

i've done that at least a half-dozen times over the years ...

---

### Post by binjured on 2006-06-14
[QUOTE=scxtt]if you can still reinstall them both w/o worrying about losing any data, i recommend this:

1. connect the disks to your mb however you want to leave them
2. partition the windows disk and install windows on the formatted/partioned master drive (SATA or IDE?)
3. install ubuntu wherever you want

while installing ubuntu, when it gets to the point where it installs grub, it should recognize your windows disk/partition and inform you of its existance before installing grub (most likely overtop of windows' MBR) ...

i've done that at least a half-dozen times over the years ...[/QUOTE]
Unfortunately I spent the better part of two days getting Ubuntu configured.  I guess if it's absolutely necessary I will do it, but man would I prefer a different solution.  Would reinstalling Ubuntu without formatting override all the packages I have installed and all that?  Is there a way I could simply reinstall Grub after switching the Windows drive to the primary and reinstalling and have it work that way?  I have configured sooo much crap on here.

---

### Post by Just4 on 2006-06-14
I dual-boot and have had no problems, but I'd think the general rule of thumb with dual booting with Windows with any distro or any other OS, is to install Windows first and then Linux? Thats how I done it and it works fine, my menu.lst looks like this:

```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin 
boot

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

I have a similar setup with SATA drives, I have sata #1 and sata #2, XP is on my first drive, single partition, sata #2 is partitioned so one part is for my Windows documents and the other for Ubuntu.

---

### Post by scxtt on 2006-06-14
[QUOTE=binjured]Unfortunately I spent the better part of two days getting Ubuntu configured.  I guess if it's absolutely necessary I will do it, but man would I prefer a different solution.  Would reinstalling Ubuntu without formatting override all the packages I have installed and all that?  Is there a way I could simply reinstall Grub after switching the Windows drive to the primary and reinstalling and have it work that way?  I have configured sooo much crap on here.[/QUOTE]it's quite possible that, if there's only a problem w/ XP's MBR, you could just reinstall XP in order to fix it (i think there's a way to clear the MBR w/o reformatting, but i haven't done it in years - something like A:\ format /MBR) - then reinstall grub on your ubuntu drive and have it correctly point to the disk XP is on ... then you wouldn't have to reformat ubuntu ... honestly, i'm not entirely sure where grub is installed (ALWAYS on /dev/hda even if linux is being installed on /dev/hdb, does it give you other options? -- i think other distros do, but ubuntu?  not so much) ...

---

### Post by binjured on 2006-06-14
Well, here's PLAN A:

1)  Use gpart to free up a little space on the Ubuntu drive.
2)  Arrange disks so XP hdd will be master, reinstall from disk
3)  Boot into Ubuntu w/ cd, reinstall Grub
4)  See what happens...

---

### Post by Bokonon on 2006-06-14
This is a bad thing?

---

### Post by binjured on 2006-06-14
Plan A:  ABORTED!

Plan B: 

1) Send case of beer to Just4 (is Heineken okay?  I'm practically swimming in the delicious lager!)

I saw the menu entry so I figured "what the hell, couldn't hurt!", restarted, and Windows launched perfectly (as perfect as it can, anyway ;))!  Thanks and cheers! =D>

[QUOTE=Bokonon]This is a bad thing?[/QUOTE]
Hahaha, for a gamer, it can be bad yes ;) 
Trust me, I will not be using Windows for anything else.

---

