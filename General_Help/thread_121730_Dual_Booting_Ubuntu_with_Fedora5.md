---
title: "Dual Booting Ubuntu with Fedora5"
date: 2006-01-25
forum: General Help
---

### Post by Edache on 2006-01-25
Hello all, this is my first post. First I would like the Ubuntu community for such great support to all. I have found a many of my concerns already answered here. Know I would like to know how I may boot a second distro with my Ubuntu distro. I have to drives. Ubuntu on the master drive mounted as hda1. I would like to put another distro on the slave drive any ideas how I can accomplish this. Thanks in advance. :smile:

---

### Post by aysiu on 2006-01-25
Easy.

Pop in Fedora.

Install it. During the installation, install Grub the MBR.

If Fedora doesn't already add Ubuntu to the boot menu (it might), mount the Ubuntu drive and find Ubuntu's Grub entry on the /boot/grub/menu.lst on Ubuntu's drive. Then copy it to the /boot/grub/menu.lst on the Fedora drive.

---

### Post by lha on 2006-01-26
[QUOTE=Edache]Hello all, this is my first post. First I would like the Ubuntu community for such great support to all. I have found a many of my concerns already answered here. Know I would like to know how I may boot a second distro with my Ubuntu distro. I have to drives. Ubuntu on the master drive mounted as hda1. I would like to put another distro on the slave drive any ideas how I can accomplish this. Thanks in advance. :smile:[/QUOTE]

I recommend you to install fedoras grub (or whatever boot loader it uses) to your slave drive. Then use chainloader in your Ubuntu's grub to load up fedora's boot loader. In this way Ubuntu and fedora will both have their own menus and if you do kernel upgrades, you don't have to manually add entries for kernels.

---

### Post by earobinson on 2006-01-26
ne idea on where to get a how to for that Iha?

---

### Post by lha on 2006-01-26
[QUOTE=earobinson]ne idea on where to get a how to for that Iha?[/QUOTE]

Hmm, maybe from me? :p

I haven't seen a how-to on this but it isn't hard at all. Last time I did this kind of setup was when I installed Dapper on my box. Dapper is installed to hdc2 and grub on hdc2's boot sector. My menu.lst has
```
title           Dapper Drake
root            (hd2,1)
chainloader     +1

```
to let me in Dapper's boot menu.

---

### Post by Edache on 2006-01-26
Thanks Iha for the response, could you tell me how I can add the lines to the (edit the)bootloader through the terminal or is there a way to do it directly in the filesystem.

Also My other porblem is that I cannot access the second drive from Ubuntu. Is there a command I can use to mount the drive and be able to edit within it.

Thanks

---

### Post by lha on 2006-01-27
[QUOTE=Edache]Thanks Iha for the response, could you tell me how I can add the lines to the (edit the)bootloader through the terminal or is there a way to do it directly in the filesystem.[/QUOTE]

First, you want to make a backup of your menu.lst.
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
Then use
```
sudo gedit menu.lst
```. Add your own menu entries under
```
### END DEBIAN AUTOMAGIC KERNELS LIST
``` or they will be erased when you upgrade kernel.

[QUOTE=Edache]Also My other porblem is that I cannot access the second drive from Ubuntu. Is there a command I can use to mount the drive and be able to edit within it.

Thanks[/QUOTE]

Yes, there is. It is 'mount'. :p Try
```
man mount
``` for info. If you post output of
```
sudo fdisk -l
```, I'll help you to edit fstab to automatically mount second drive when you start your computer.

---

### Post by Edache on 2006-01-27
Thanks again Iha, I will post my results later. :cool:

---

### Post by Edache on 2006-01-28
for info. If you post output of
```
sudo fdisk -l
```, I'll help you to edit fstab to automatically mount second drive when you start your computer.[/QUOTE]

Hello All thanks for your help with the dual booting issue. I did get it to work with Iha and aysiu help. Love the challenge of getting linux to work, with people like you guys help, it keeps me in the game. Thanks again.

Now Iha for your help on auto mounting second drive. this is my output.

 Disk /dev/hda: 15.3 GB, 15364339200 bytes
255 heads, 63 sectors/track, 1867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1787    14354046   83  Linux
/dev/hda2            1788        1867      642600    5  Extended
/dev/hda5            1788        1867      642568+  82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
240 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          14      105808+  83  Linux
/dev/hdb2              15        1092     8149680   8e  Linux LVM

Thanks again

---

### Post by lha on 2006-01-28
Your hdb1 is quite small, did you use it as a /boot partition? It's only ~100MB. If you are interested in it, use
```
sudo mount /dev/hdb1 /some/directory
``` to mount it. Then type
```
mount
``` This tells you the right filesystem. Eg. line
```
/dev/hdb1 on /mnt type jfs (rw)
```
tells you hdc2 is mounted on /mnt, its filesystem is jfs and writing to that drive is not prohibited. You will likely see ext2 or ext3 instead of jfs. Open fstab and add
```
/dev/hdb1 /some/directory jfs defaults 0 0
```
Remember to change jfs to whatever you saw before.

As of hdb2, I have made too big a promise. :( I have no experience with LVM, so I cannot help you with that. Sorry.

---

