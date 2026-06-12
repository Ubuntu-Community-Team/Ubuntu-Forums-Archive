---
title: "GRUB loading stage 1.5 Error 15 Ubuntu 9.10"
date: 2009-12-27
forum: General Help
---

### Post by Ottis on 2009-12-27
Dual boot XP home and Ubuntu, Dell Optiples 210L, 80Gb sata and 250Gb IDE slave. Both XP and Ubuntu on the 80Gb sata drive.
-------
I just finished reinstalling Ubuntu 9.10 from the CD after a failed attempt to upgrade 9.04 to 9.10 on-line.
I deleted the old ext3 and swap partitions first with an old GParted live CD (0.4.4-1i) and then reinstalled 9.10 onto the unallocated space.  Everything went smooth till reboot, then all I get was this;

GRUB loading Stage1.5.
GRUB loading, please wait...
ERROR 15

I had to reinstall GRUB once on my PC that dual boots XP and ubuntu 8.04, but this seems to be different. How can I fix this???

Edit; There's no "menu.lst" file in my boot/grub folder (?)

---

### Post by Ottis on 2009-12-27
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04a46f60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3711    29808576    c  W95 FAT32 (LBA)
/dev/sda2            3712       30401   214387425    f  W95 Ext'd (LBA)
/dev/sda5            3712       30401   214387393+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6        7176    57601057+   7  HPFS/NTFS
/dev/sdb3            7177        9726    20482875    5  Extended
/dev/sdb5            7177        9614    19583203+  83  Linux
/dev/sdb6            9615        9726      899608+  82  Linux swap / Solaris

---

### Post by Barriehie on 2009-12-27
This seems to happen frequently... [http://ubuntuforums.org/showthread.php?t=644773](http://ubuntuforums.org/showthread.php?t=644773)

FWIW I never let anything change my menu.lst file!
Barrie

Edit: Please post your menu.lst file. /boot/grub/menu.lst

---

### Post by Ottis on 2009-12-27
I was just looking for that, there is no "menu.lst" file in my boot/grub folder...

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> I was just looking for that, there is no "menu.lst" file in my boot/grub folder...

Well then let's see if if there's a menu.*anything*; perhaps it was backed up/renamed before it got hosed.
```

sudo find / -iname menu.* -print

```

Barrie

---

### Post by Ottis on 2009-12-27
Nothing by that name in the boot/grub folder, nothing named menu.anything

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> Nothing by that name in the boot/grub folder, nothing named menu.anything

I should've been more specific :( I meant like menu.*, or better yet menu*

```

sudo find / -iname menu* -print

```

Barrie

---

### Post by Ottis on 2009-12-27
I understood, :P there's nothing named menu.... with any extension.
I just looked on my brother-in-laws PC which I have setting here, it's dual booting XP and Super Ubuntu (9.10) (trying to get dual monitors to work under ubuntu:( ) It has the menu.lst file.. so i guess the new version of grub isn't that different...

---

### Post by Barriehie on 2009-12-27
Try booting from a live CD and get to a terminal.  Then,

```

sudo grub
>root (hd0,0)
>setup (hd0)
>exit

```

Barrie

---

### Post by Ottis on 2009-12-27
root@ubuntu:~# sudo grub
sudo: grub: command not found


BTW, Im posting from firefox on the live CD

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> root@ubuntu:~# sudo grub
sudo: grub: command not found


BTW, Im posting from firefox on the live CD

Well, this might be better than snafu...  wait one!

Barrie

---

### Post by Ottis on 2009-12-27
Typed in ; root@ubuntu:~# grub
Came back that grub wasn't installed, (?) so I installed it.....
trying the rest of your suggestion now

---

### Post by Barriehie on 2009-12-27
This post might just fix you...

[http://ubuntuforums.org/showthread.php?t=1359636&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=1359636&highlight=reinstall+grub)

> **garyed said:**
> I'm assuming you're not getting a grub menu any more but if I'm wrong then these steps are not needed:
Anyways:
Boot from the 9.10 live CD, open a terminal & do:

```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
then reboot, take out the CD & hopefully you'll get a grub menu to get you back into Ubuntu. Once there get to a terminal & do:
[CODE]sudo update-grub[CODE]

If that doesn't work you could try to substitute hda.. for sda..

---

### Post by Ottis on 2009-12-27
In terminal I now have;

Grub>

Will those commands work for my dual boot setup? (with 2 HDDs?)

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> In terminal I now have;

Grub>

Will those commands work for my dual boot setup? (with 2 HDDs?)

It looks like, from your earlier post that sdb5 is your linux/boot partition?  If so substitute /dev/sdb5 instead of /dev/*whatever*.

Barrie

---

### Post by Ottis on 2009-12-27
I got this;

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> I got this;

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$

Well it looks as if you're better off than 20 min. ago!  See if it boots!

Barrie

---

### Post by Ottis on 2009-12-27
rebooted; Im posting from a different PC now.
I get this at boot.


[Minimas BASH-like line editing is supported.  for
the first word, TAB lists possable command
completions. Anywhere else TAB lists the possible
completions of a device/ filename.  ]

grub>

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> rebooted; Im posting from a different PC now.
I get this at boot.


[Minimas BASH-like line editing is supported.  for
the first word, TAB lists possable command
completions. Anywhere else TAB lists the possible
completions of a device/ filename.  ]

grub>

So it booted without an error; short of not finding the boot kernel.  Probably installed on the wrong partition.  Let's look for a menu.lst file and post please.

Barrie

---

### Post by Ottis on 2009-12-27
Ok, rebooting to live cd

---

### Post by Ottis on 2009-12-27
no, still no menu.lst

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> no, still no menu.lst

Well I'm out of ideas now.  How about booting from the live CD and reinstalling??? or wait for a more adept poster! :)

Barrie

---

### Post by Ottis on 2009-12-27
I rebooted to the live cd and now its back to 

grub: command not found

I checked the disc for errors before installing, is it possible that there's something wrong with the "grub" on the disk?

Can I use another disc to install grub onto my HDD?

---

### Post by Barriehie on 2009-12-27
> **Ottis said:**
> I rebooted to the live cd and now its back to 

grub: command not found

I checked the disc for errors before installing, is it possible that there's something wrong with the "grub" on the disk?

Can I use another disc to install grub onto my HDD?

Go with another disk.  I have to work tonight so it's off to bed for me.  I'll look in again later.

Barrie

---

### Post by Ottis on 2009-12-27
Thanks for the help, I think I'll redownload and burn a new disc, start over again tomorrow.

Thanks for the help!!!:P

---

### Post by Barriehie on 2009-12-28
> **Ottis said:**
> Thanks for the help, I think I'll redownload and burn a new disc, start over again tomorrow.

Thanks for the help!!!:P

Let us know how it goes and what you end up doing!

Barrie

---

### Post by Leppie on 2009-12-28
> **Ottis said:**
> no, still no menu.lst
Karmic ships with GRUB2 which uses grub.cfg instead of menu.lst. menu.lst would only appear after an upgrade.

Normally one wants to boot off the first hd (hda or sda), but you were trying to install grub2 to the mbr of sdb so i've adapted the instructions to that.
Boot using your livecd, then issue these commands:
```
$sudo mkdir /mnt/temp  ##create mount point
$sudo mount /dev/sdb5 /mnt/temp  ##mount your filesystem
$sudo cp /mnt/temp/boot/grub/device.map /mnt/temp/boot/grub/device.map.old  ##make a backup of your device.map
$sudo grub-install --root-directory=/mnt/temp /dev/sdb  ##install grub2 to the mbr of sdb
$sudo update-grub  ##regenerate grub.cfg
```

---

### Post by andru183 on 2010-03-04
i followed the previous post but when i got to
sudo grub-install --root-directory=/mnt/temp /dev/sdb
i got

Installation finished. No error reported.
This is the contents of the device map /mnt/temp/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

and cant contuine and dont understand how to contuine

---

