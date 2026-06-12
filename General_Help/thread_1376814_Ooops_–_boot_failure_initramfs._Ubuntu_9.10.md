---
title: "Ooops – boot failure: initramfs. Ubuntu 9.10"
date: 2010-01-09
forum: General Help
---

### Post by fisheater on 2010-01-09
Ooops &#8211; boot failure: initramfs

Hi, my (mis)adventure with linux continues.

Problem: can&#8217;t boot my 9.10 laptop. Tried in recovery mode, and with previous kernels/recovery modes.

Background: recently installed nomachine VNC system two days ago &#8211; was working up to today. 

When I boot this is what happens.
-Grub
(select most recent kernel)
-Ubuntu ring
-Black screen
-Then this message:
render error detected, EIR: 0x00000010
page table error
PGTBL_ER: 0x00000100
[drm:i915_handle_error] *ERROR* EIR stuck 0x00000010, masking
render error detected, EIR 0x00000010
page table error
PGTBL_ER: 0x00000100
[drm] LVDS-8: set mode 1280x768 17
Console: switching to colour frame buffer device 160x48

Gave up waiting for root device.

ALERT:! /dev/disk/by-uuid/ (crazy long number, retyping by hand) does not exist. Dropping to shell.

Busybox v1.13.3
-(initramfs)

Then I am stuck.

This is way above me, but I have tried to get some insight from a deep google search. I need to get a LiveCD and try some of these workarounds:
[http://ubuntuforums.org/showthread.php?t=1275627](http://ubuntuforums.org/showthread.php?t=1275627)

[http://ubuntuforums.org/showthread.php?t=1230498](http://ubuntuforums.org/showthread.php?t=1230498)

Please let me know if you have any suggestions! I *just copied all my files to my NAS last night, the only thing not backed up are my bookmarks. Worse case, I can reinstall, but am hoping to fix it without that.

Thanks,

FE

---

### Post by ibuclaw on 2010-01-09
> **fisheater said:**
> Ooops – boot failure: initramfs

Hi, my (mis)adventure with linux continues.

Problem: can’t boot my 9.10 laptop. Tried in recovery mode, and with previous kernels/recovery modes.

Background: recently installed nomachine VNC system two days ago – was working up to today. 

When I boot this is what happens.
-Grub
(select most recent kernel)
-Ubuntu ring
-Black screen
-Then this message:
render error detected, EIR: 0x00000010
page table error
PGTBL_ER: 0x00000100
[drm:i915_handle_error] *ERROR* EIR stuck 0x00000010, masking
render error detected, EIR 0x00000010
page table error
PGTBL_ER: 0x00000100
[drm] LVDS-8: set mode 1280x768 17
Console: switching to colour frame buffer device 160x48

Gave up waiting for root device.

ALERT:! /dev/disk/by-uuid/ (crazy long number, retyping by hand) does not exist. Dropping to shell.

Busybox v1.13.3
-(initramfs)

Then I am stuck.

This is way above me, but I have tried to get some insight from a deep google search. I need to get a LiveCD and try some of these workarounds:
[http://ubuntuforums.org/showthread.php?t=1275627](http://ubuntuforums.org/showthread.php?t=1275627)

[http://ubuntuforums.org/showthread.php?t=1230498](http://ubuntuforums.org/showthread.php?t=1230498)

Please let me know if you have any suggestions! I *just copied all my files to my NAS last night, the only thing not backed up are my bookmarks. Worse case, I can reinstall, but am hoping to fix it without that.

Thanks,

FE

Well, lets start from the top.

I am assuming this is a malconfigured fstab issue in the first instance.

Boot from a **LiveCD**, and copy the following commands into a terminal:
```
sudo fdisk -l
```
```
sudo blkid
```
Then copy the output and paste it here in [CODE] tags.

Regards
Iain

---

### Post by fisheater on 2010-01-09
Tinivole,

Thanks for your help, this is digging deep into my computer and beyond me!

sudo fdisk -l

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x089c4586

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/sda2            5230       12137    55488510    5  Extended
/dev/sda5            5230       11849    53175118+  83  Linux
/dev/sda6           11850       12137     2313328+  82  Linux swap / Solaris

sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D212D6BAD133F66B" LABEL="Orange" TYPE="ntfs" 
/dev/sda5: UUID="9fafae24-89e8-4c4f-85d6-edb640afe648" TYPE="ext4" 
/dev/sda6: UUID="a884479b-c360-4874-b472-2d24424b8457" TYPE="swap" 

Regards,

FE

---

### Post by fisheater on 2010-01-09
More:

I tried to fsck and e2fsck via LiveCD to see if there was an issue there.

sudo fsck -v -f /dev/hda2
sudo fsck -v -f /dev/hda5
sudo fsck -v -f /dev/hda6

and 

sudo e2fsck /dev/hda2 -y -f
sudo e2fsck /dev/hda5 -y -f
sudo e2fsck /dev/hda6 -y -f

Yielded:

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/hda* (all of the 6 above combinations)

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I was able to mount my drive via a liveCD so that is still working. Again the only thing that I would like to save (if I have to rebuild) is my firefox bookmarks. Any suggestions where they are stored?

Thanks!

FE

---

### Post by fisheater on 2010-01-09
I did a fresh install of 9.04. Thanks for the help.

FE

---

### Post by ibuclaw on 2010-01-10
> **fisheater said:**
> Tinivole,

Thanks for your help, this is digging deep into my computer and beyond me!

sudo fdisk -l

Disk /dev/sda: 99.8 GB, 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x089c4586

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/sda2            5230       12137    55488510    5  Extended
**/dev/sda5            5230       11849    53175118+  83  Linux**
/dev/sda6           11850       12137     2313328+  82  Linux swap / Solaris

sudo blkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D212D6BAD133F66B" LABEL="Orange" TYPE="ntfs" 
**/dev/sda5: UUID="9fafae24-89e8-4c4f-85d6-edb640afe648" TYPE="ext4"** 
/dev/sda6: UUID="a884479b-c360-4874-b472-2d24424b8457" TYPE="swap" 

Regards,

FE

As you can see from the output (I've highlighted the interesting lines), /dev/sda5 is your root Linux partition, and the UUID of the partition (Unique Identifier) is "9fafae24-89e8-4c4f-85d6-edb640afe648".

What you would do next is mount the filesystem.

```
sudo mount /dev/sda5 /mnt
```
Check it's fstab
```
sudo nano /mnt/etc/fstab
```
And compare the UUID in the fstab file to the UUID that blkid is showing. If different, update it, save and reboot.

If they are both the same - or if you can't mount the filesystem, try a fsck.

To do this would be:
```
sudo fsck -fyv /dev/sda5
```

> **fisheater said:**
> More:

I tried to fsck and e2fsck via LiveCD to see if there was an issue there.

sudo fsck -v -f /dev/hda2
sudo fsck -v -f /dev/hda5
sudo fsck -v -f /dev/hda6

and 

sudo e2fsck /dev/hda2 -y -f
sudo e2fsck /dev/hda5 -y -f
sudo e2fsck /dev/hda6 -y -f

Yielded:

fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: No such file or directory while trying to open /dev/hda* (all of the 6 above combinations)

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I was able to mount my drive via a liveCD so that is still working. Again the only thing that I would like to save (if I have to rebuild) is my firefox bookmarks. Any suggestions where they are stored?

Thanks!

FE
Ah, you are still living in the old ages. ;)

The device names have changed from hda, hdb, hdc... to **sda**, **sdb**, **sdc**... for quite a while now (probably since 2.6.20-ish times). You were trying to fsck the wrong device. ;)
> **fisheater said:**
> I did a fresh install of 9.04. Thanks for the help.

FE
That is the easy way out - you didn't need to have to do this (though - looking at the time you posted, I would have been sleeping at the time). Oh well...

I hope I've left you enough information to try and tackle this yourself if it were to happen again.

Regards
Iain

---

### Post by fisheater on 2010-01-10
No worries, I see the error that I was making.

All is not lost, my laptop seems to be happier running 9.04. I was stuck to get it running, I am going to be away for a month and needed my access to be up and running quick. If I had more time I would have poked around a bit more.

Thanks again for your suggestions!

FE

---

### Post by Chaconne on 2011-03-28
Thank you very much ibuclaw. I encountered the same problem and sudo fsck -fyv saved me!

---

