---
title: "Lost my data?"
date: 2010-02-09
forum: General Help
---

### Post by deLiz on 2010-02-09
:-(

Okay Guys, today when I enter Ubuntu as usual, i get on the screen to log on then i insert my login data, and the pc froze up. I try again and nothing. Came to mind that would be HD bad-blocks, which have a long and boring history with them.

Okay, I log on Windows, I do some stuff, then I go back to ubuntu, and same thing. I've tried running fsck in the shell (recovery option on grub) , but has not had any results. The fsck just tried, but it get some error or something.

After fsck I restart, the screen show ERROR 17 in Grub, had given it before, I thought it was nothing, just reinstall grub. Ok

So i put the ubuntu liveCD to try to recover Grub, and the Grub was like impossible to recover or install. Nice to mention that i was checking the HD's to see if everything was straight, and only came to the Windows partition, ubuntu partition did not appear. I had noticed that was strange, but ok.

After a while i managed to recover the Windows MBR, then I want to use explore2fs to save some files from ubuntu and then format the entire hard drive, but nothing, had no unit available to chose there, all in white, no options, no hda or sda.

I lost everything? It is not possible, I have too many things there, they can not be thrown away :(

Please, give me some sort of light! 

Grateful

ps: sorry for the bad english
ps2: oh, sorry if i post this on the wrong section of the board

---

### Post by jken146 on 2010-02-09
Boot up your live CD, open a terminal and type ```
sudo fdisk -l
```
You should see a list of disks and partitions. Hopefully there will be (at least) one identified as 'Linux' which you can then mount with the command **mount**.

---

### Post by deLiz on 2010-02-15
> **jken146 said:**
> Boot up your live CD, open a terminal and type ```
sudo fdisk -l
```
You should see a list of disks and partitions. Hopefully there will be (at least) one identified as 'Linux' which you can then mount with the command **mount**.

so, i got my partitions. ntfs, extended, swap.

Extended is on /dev/sda4

so i do - 

sudo mount /dev/sda4

than i got -

mount: can't find /dev/sda4 in /etc/fstab or /etc/mtab

..

Than i do - 

sudo mount /dev/sda4 /media/disk

and got -
mount: you must specify the filesystem type

..

Than i do - 

sudo mount -t ext2 /dev/sda4 /media/disk

and got -
mount: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error (aren't you trying to mount an extended partition, instead of some ogical partition instead?)
In some cases useful info is found in syslog - try
dmesg | tail or so

---

---

### Post by jken146 on 2010-02-15
The extended partition is just a container for the logical partition which is formatted as swap. It doesn't actually contain a filesystem of its own.

If you could post the output of ```
sudo fdisk -l
``` we can see if there is a big gap on the disk where your / partition should be, and set about getting it back.

---

### Post by deLiz on 2010-02-15
> **jken146 said:**
> The extended partition is just a container for the logical partition which is formatted as swap. It doesn't actually contain a filesystem of its own.

If you could post the output of ```
sudo fdisk -l
``` we can see if there is a big gap on the disk where your / partition should be, and set about getting it back.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa820a820

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13 102400 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 13 1658 13209600 6 FAT16
Partition 2 does not end on cylinder boundary.
/dev/sda3 1658 5099 27643904 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4 5100 9733 37222605 5 Extended
/dev/sda5 5100 9546 35720496 83 Linux
/dev/sda6 9547 9733 1502046 82 Linux swap / Solaris

---

### Post by ironclaw on 2010-02-15
/dev/sda5 should be your Linux root partition. Can you try mounting it on a live CD?
```
sudo mkdir /mnt/tmpmnt/
sudo mount /dev/sda5 /mnt/tmpmnt/
```

---

### Post by deLiz on 2010-02-16
> **ironclaw said:**
> /dev/sda5 should be your Linux root partition. Can you try mounting it on a live CD?
```
sudo mkdir /mnt/tmpmnt/
sudo mount /dev/sda5 /mnt/tmpmnt/
```


> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/tmp
mount: you must specify the filesystem type


> ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sda5 /mnt/tmp
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



i tried mounting as ext2 and ext3, same error


ps: maybe useful

> ubuntu@ubuntu:~$ sudo file -s /dev/sda5
/dev/sda5: ACB archive data


---

### Post by audiomick on 2010-02-16
If it was a fresh install of 9.10, the file system will be ext4 unless you specified otherwise.

---

### Post by ironclaw on 2010-02-16
It might be a corrupted ext3 or ext4 file system. To try to correct it:
```
sudo e2fsck -p /dev/sda5
```
This will call e2fsck to automatically check and repair the file system.

Then try mounting sda5 again.

---

### Post by deLiz on 2010-02-16
> **audiomick said:**
> If it was a fresh install of 9.10, the file system will be ext4 unless you specified otherwise.

no, it is 8.04 :/

> **ironclaw said:**
> It might be a corrupted ext3 or ext4 file system. To try to correct it:
```
sudo e2fsck -p /dev/sda5
```
This will call e2fsck to automatically check and repair the file system.

Then try mounting sda5 again.


i will try that, brb

---

### Post by deLiz on 2010-02-16
> ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda5
e2fsck: Bad magic number in super-block while trying to open /dev/sda5
/dev/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

should i do that?

---

### Post by ironclaw on 2010-02-16
Yes, try using an alternate superblock. It may be that the normal superblock is corrupted.
```
sudo e2fsck -p -b 8193 /dev/sda5
```

---

### Post by deLiz on 2010-02-16
> **ironclaw said:**
> Yes, try using an alternate superblock. It may be that the normal superblock is corrupted.
```
sudo e2fsck -p -b 8193 /dev/sda5
```

yay, i shutdown for like 5 hours and just try e2fsck and it fixed it! :D:D:D

thank you boys!

---

