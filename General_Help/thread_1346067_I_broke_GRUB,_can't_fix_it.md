---
title: "I broke GRUB, can't fix it"
date: 2009-12-04
forum: General Help
---

### Post by blaher on 2009-12-04
I was working on Windows Vista's disk manager and I accidentally right-clicked on extend on the Window's partition. I have no idea what it did, but it asked me to format my Linux partition and I said no. When I restarted, GRUB gave me a #17 error. I went to a old live CD (8.10) and tried to fix it. I used cfdisk to change the linux partition from EXTENDED to LINUX and made it bootable instead of the Windows partition. I then tried using grub, used:

```
sudo grub
grub> root (hd0, 4)
grub> setup (hd0)
```

...and I get...

```
Error 17: Cannot mount selected partition

```

Here is my 'fdisk -l' results:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
64 heads, 32 sectors/track, 305245 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xc462e0a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      254357   260461548    7  HPFS/NTFS
/dev/sda2          254358      290136    36637696    5  Extended
/dev/sda3          290137      305245    15471616   12  Compaq diagnostics
/dev/sda5   *      254358      285015    31393791+  83  Linux
/dev/sda6          285017      290136     5242864    7  HPFS/NTFS

```

I really have no idea how to fix this. I can't even boot in to windows without grub working and I have no vista disk. sda5 is my 9.10 and I really need a lot of data on it for school. sda1 is windows, sda2 I have no idea what it is and it doesn't show up in cfdisk, sda3 came with my laptop.

Here is my search results in grub, if it provides helpful:

```
grub> root (hd0,4) 

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /boot/stage1

Error 15: File not found

```

---

### Post by wendell123 on 2009-12-04
I am having a problem with grub as well I have a dual boot on my laptop with WXP
and dont know how to get umbutu to boot again

---

### Post by wendell123 on 2009-12-04
> **wendell123 said:**
> I am having a problem with grub as well I have a dual boot on my laptop with WXP
and dont know how to get umbutu to boot again What command should I use??????

---

### Post by carlinuxlearner on 2009-12-04
@ blaher
You did it wrong, it's 
```
sudo grub
```
then enter this:
```
find /boot/grub/stage1
```

And you can follow the rest of the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by blaher on 2009-12-04
> **carlinuxlearner said:**
> @ blaher
You did it wrong, it's 
```
sudo grub
```
then enter this:
```
find /boot/grub/stage1
```

And you can follow the rest of the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
I did that too, it's even in my post.

---

### Post by carlinuxlearner on 2009-12-04
Yes, but you did it in the wrong order.

You did this:
```
sudo grub
grub> root (hd0, 4)
grub> setup (hd0)

```

And this:
```
grub> root (hd0,4) 

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /boot/stage1

Error 15: File not found
```

What you **need** to do is this:
```
sudo grub
grub> find /boot/grub/stage1
grub> root (hd$,*)
grub> setup (hd0)

```

*replace with whatever the "find /boot/grub/stage1" gave you
$replace with whatever the "find /boot/grub/stage1" gave you

---

### Post by blaher on 2009-12-04
It still gives me a "Error 15: File not found". I did it your way and I get the same results, I don't think the order effects find.

---

### Post by Leppie on 2009-12-04
@Blaher, install GRUB to the mbr:
```
$sudo grub-install --recheck /dev/sda
```

there's plenty of dos boot disks on the net with the fdisk utility. a simple fdisk /mbr command in dos will restore the master boot record to factory defaults (and let you boot windoze after you've set it's partition to bootable).

---

### Post by blaher on 2009-12-04
> **Leppie said:**
> @Blaher, install GRUB to the mbr:
```
$sudo grub-install --recheck /dev/sda
```

there's plenty of dos boot disks on the net with the fdisk utility. a simple fdisk /mbr command in dos will restore the master boot record to factory defaults (and let you boot windoze after you've set it's partition to bootable).

When I did that, I get:

```
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

I'll try getting a dos disk somewhere are trying the second thing.

---

### Post by carlinuxlearner on 2009-12-04
"It still gives me a "Error 15: File not found"."
:|
If it's still giving that error... heh, are you SURE you didn't reformat it? 

"I don't think the order effects find."
Heh, the "find /boot/grub/stage1" **defines** what you put in "root (hd$,*)" so it makes a big difference. But (as in this case) if there is **no** grub stage 1 to find, it will still result in the same error.

---

### Post by Leppie on 2009-12-04
@Blaher, did you mount the linux partition when trying to re-install grub?
```
$sudo mkdir -p /mnt/temp
$sudo mount /dev/sda5 /mnt/temp
$sudo chroot /mnt/temp
$sudo grub-install --recheck /dev/sda
```

---

### Post by Some Penguin on 2009-12-04
Are you sure / refers to your main filesystem, not to the filesystem on the live CD that you've booted?  If it's the latter, you can either

1) attempt to boot off the live CD while specifying a different root partition, or
2) chroot.

---

### Post by blaher on 2009-12-04
> **Leppie said:**
> @Blaher, did you mount the linux partition when trying to re-install grub?
```
$sudo mkdir -p /mnt/temp
$sudo mount /dev/sda5 /mnt/temp
$sudo chroot /mnt/temp
$sudo grub-install --recheck /dev/sda
```

I get this.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/temp
mount: you must specify the filesystem type

```

---

### Post by blaher on 2009-12-04
Well, I managed to install a windows boot loader, so at least I can boot in to something now. I guess I could do a fresh install with Ubuntu, but I really need to get some projects files out first. I need to know how to mount the partition and grab some files, please help.

---

### Post by carlinuxlearner on 2009-12-04
As far as mounting your ext3 filesystems in windows, this should work:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

I know it says ext2, but it seems to work just fine reading ext3. (go figure)

---

### Post by Leppie on 2009-12-05
> **blaher said:**
> I get this.
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/temp
mount: you must specify the filesystem type

```

If you haven't changed the default file system during installation of Karmic, I believe you should have ext4. I changed it to jfs, but think I saw ext4 flashing by in gparted during installation.
So the mount command would be like this:
```
$sudo mount -t ext4 /dev/sda3 /mnt/temp
```

---

