---
title: "HELP - GRUB Error 17"
date: 2010-03-18
forum: General Help
---

### Post by zeug on 2010-03-18
Initially I had have my hard-drive setup in such a way that Vista was on /dev/sda3 and Ubuntu 9.04 was on /dev/sda4.  I used EasyBCD to create an entry in the Windows bootloader to include chainloader of the Ubuntu partition.
After installing Windows 7 on /dev/sda3 partition after deleting it with the Windows setup and formatting it at a smaller size, I installed EasyBCD again so I could boot my Ubuntu partition.  However, this no longer worked and NeoGrub reported errors like "Error 17 - File not found".  Playing around for a bit trying to find out what happened, it seems the the Windows disk manager recognizes the Ubuntu "partition" as unallocated.  I then tried to use boot onto an Ubuntu live CD so I could setup GRUB on the Ubuntu partition again.  However, after trying to mount the partition /dev/sda4, as suggested by this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) , it returns an error saying it cannot be mounted (as EXT4 or EXT3)
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/part/
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```Is there any way to fix this?  I really can't tell what is wrong anymore and I really do not know what caused it.

Thanks.

---

### Post by Ozymandias_117 on 2010-03-18
Can you please post the results of ```
sudo fdisk -l
```

---

### Post by zeug on 2010-03-18
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317       14065   102400000    7  HPFS/NTFS
/dev/sda4           25098       30401    42604380    5  Extended
/dev/sda5           30156       30401     1975995   82  Linux swap / Solaris

```

---

### Post by Ozymandias_117 on 2010-03-18
Er... According to fdisk there is no linux partition o.O Um... sorry, I'm afraid I'm not sure what to tell you...

---

### Post by oldfred on 2010-03-18
sda4 is the extended partition which is just a container for more partitions and currently has your swap partition in it.

Testdisk may show you old partition info, but if you installed win7 over your ubuntu it will be easier just to create a new partition and reinstall.

---

### Post by zeug on 2010-03-19
I found this thread after posting this one. [http://ubuntuforums.org/showthread.php?t=1154829&page=2](http://ubuntuforums.org/showthread.php?t=1154829&page=2)  It does talk about using testdisk.  I do not think I installed Windows over Ubuntu because I do not select the Ubuntu partition when installing it.  Thanks both of you!

---

### Post by zeug on 2010-03-19
Okay, I found my partition with testdisk but, when I try to boot into it, all I get is the GRUB prompt and nothing else.  I did run ```
find /boot/grub/stage1
``` and it returned a ```
(hd0,3)
```  I thought I would try booting from this partition in the GRUB prompt with
```

root (hd0,3)
chainloader +1
boot

```
but it would just give me the GRUB prompt again.

I tried ```
setup (hd0,3)
``` but it return error 22, partition not found.

Also, when I did restore with testdisk, I could get every partition back EXCEPT my swap partition (it would let me make it a logical partition).

Any ideas?

Thanks!

---

### Post by oldfred on 2010-03-19
If you got everything but swap back you are in good shape. swap does not have any data in it. You can create a new swap and go into your install's fstab to edit the UUID to be the correct UUID for the new swap.

To see UUID
sudo blkid

---

### Post by zeug on 2010-03-19
I got it to boot finally, I just needed to
```
root (hd0,3)
setup (hd0,3)
```
instead of just the setup command.

About getting the swap partition back, how would I do that?  Currently, the part of the disk that had the swap is marked as unallocated.

---

### Post by zeug on 2010-03-19
It seems that GRUB installed to the MBR anyway.  How does one install GRUB to the partition, then?

I am still at a loss with swap, too.

Thanks.

---

### Post by oldfred on 2010-03-19
Grub2 does not like to install to a partition but I have had not problem installing grub legacy to a partition. Adjust entries below to your drive/partition numbers remember old grub counts partitions starting at zero.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)
# Or
6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
quit

You can use gparted to create a new swap, but you will have to edit fstab to have the new UUID.

---

### Post by zeug on 2010-03-19
I did 
```
sudo grub
grub> find /boot/grub/stage1
 (hd0,3)

grub> setup (hd0,3)

Error 12: Invalid device requested

```With ```
 root (hd0,3) 
``` before the setup command, setup does work (finding e2fs_stage1_5 or something similar fails, though).

I looked in gparted, but it will not let me add another partition as swap because it wants to add it as a primary partition and I have too many of those already.

---

### Post by oldfred on 2010-03-19
Did you miss the root command in the sequence?

If you have used all 4 partitions as primary you cannot add any more. You need 3 primary and make the fourth as an extended so you can add many logical partitions inside the extended. It usually is a big hassle to redo if you have used all four.

---

### Post by zeug on 2010-03-19
Yeah, I missed the root command and it worked after putting it.

About the extended partition, it was extended before I restored.  I should be able to fix that with testdisk, though?  It found the swap partition last time.

Thanks.

---

