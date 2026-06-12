---
title: "Error: no such device: af1b622e-4651-4ccd-959a-cb684df49e64"
date: 2010-01-11
forum: General Help
---

### Post by hunterkasy on 2010-01-11
I am trying to install xubuntu 9.10 on a machine, when I boot with the xubuntu 9.10 cd I select install, instead of taking me to the install process it takes me to the live cd, also during that time It goes to, I guess what I would call terminal, while it is loading, during that time I am seeing allot of buffer I/O errors SRO on the sector and logical, after all of that It goes to the live cd, then it has a crash report, then that takes me to what I believe is closest to what I have bug: 441904 reading through the comments of that bug, they were talking about it should be fixed on the final 9.10,  I go through the install on the live cd, (clicking on install on the desktop) everything goes fine, after that I do notice another crash report, bug# 452208 I reboot like it ask, take out the cd and when the grub tries to load I get this: 

Error: no such device: af1b622e-4651-4ccd-959a-cb684df49e64 failed to boot default entries

I did have xubuntu 9.04 upgraded to 9.10 installed on the same machine, I wanted the newest partition format, so that is why I am trying to do this clean install

also, reading in the bug report someone was saying their cd player was faulting and that was giving them the I/O's, I replaced the old cd player with a new dvd/cd player and still problems

---

### Post by hunterkasy on 2010-01-11
bump

---

### Post by Leppie on 2010-01-11
did you check the cd for errors?
can you boot normally using the livecd? if so, please post the output of the following command:
```
sudo blkid
```

---

### Post by hunterkasy on 2010-01-11
Yes, I can boot into a live cd, I did re-burn the xubuntu 9.10 image onto a new cd at 4x and I had it verify the image, everything went fine with that.

buntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="fa203dcd-aa3d-48f2-aa25-a3bc0f488538" TYPE="ext4" 
/dev/sda5: UUID="47317fbb-38c6-4f8b-ae10-83e5f1962ce3" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/ramzswap0: TYPE="swap" 
ubuntu@ubuntu:~$

---

### Post by hunterkasy on 2010-01-11
Does anyone have anymore idea's?

---

### Post by Leppie on 2010-01-11
> **hunterkasy said:**
> bump
you may want to check the forum rules and read up on how to bump correctly...

---

### Post by Leppie on 2010-01-11
booting with the livecd, execute the following commands:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

reboot to see if the menu appears correctly and you can boot into all your os's normally.

---

### Post by hunterkasy on 2010-01-11
> **Leppie said:**
> booting with the livecd, execute the following commands:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda1 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
grub-install --recheck /dev/sda
update-grub
exit
```

reboot to see if the menu appears correctly and you can boot into all your os's normally.


I tried that, and when I boot from the hhd drive it still gives me this message: Error: no such device: af1b622e-4651-4ccd-959a-cb684df49e64 failed to boot default entries

---

### Post by Leppie on 2010-01-11
could you post the output of the following commands:
```
sudo mount /dev/sda5 /mnt
sudo blkid -c /mnt/etc/blkid.tab
```

---

### Post by hunterkasy on 2010-01-11
> **Leppie said:**
> could you post the output of the following commands:
```
sudo mount /dev/sda5 /mnt
sudo blkid -c /mnt/etc/blkid.tab
```

using the live cd of xubuntu 9.10

root@ubuntu:~# sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
root@ubuntu:~# 

root@ubuntu:~# sudo blkid -c /mnt/etc/blkid.tab
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="faf6c23d-db53-4f17-879e-1fd1ed35b34f" TYPE="ext4" 
/dev/sda5: UUID="47317fbb-38c6-4f8b-ae10-83e5f1962ce3" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
root@ubuntu:~#

---

### Post by Leppie on 2010-01-11
hmm... strange...
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by hunterkasy on 2010-01-11
> **Leppie said:**
> hmm... strange...
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

here is the RESULTS.txt

---

### Post by Leppie on 2010-01-11
try the following command:
```
sudo fsck /dev/sda5
```

---

### Post by hunterkasy on 2010-01-11
> **Leppie said:**
> try the following command:
```
sudo fsck /dev/sda5
```

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
ubuntu@ubuntu:~$

---

### Post by Leppie on 2010-01-11
are you sure this disk is physically ok?
it sounds like it has some issues.
try to see if fdisk finds any errors when accessing the drive:
```
sudo fdisk /dev/sda
```
if it doesn't indicate any errors at launch, just quit (press "q").

---

### Post by hunterkasy on 2010-01-11
> **Leppie said:**
> are you sure this disk is physically ok?
it sounds like it has some issues.
try to see if fdisk finds any errors when accessing the drive:
```
sudo fdisk /dev/sda
```
if it doesn't indicate any errors at launch, just quit (press "q").

ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):

---

### Post by hunterkasy on 2010-01-12
Well, all I know is, I re-downloaded the xubuntu 9.10 from the site, burned at the slowest possible rate and also had it verify the image everything went fine completed no problems, I still get the same issues on the same machine listed above, so I took that same cd and put it into another pc and booted it to the cd, selecting install, from the cd, brought me up to the install pages, installs just fine on that other machine, so I now know it is not the cd, I have determined it is the xubuntu 9.10 installation is the problem, I am able to install xubuntu 9.04 on the same computer that will not take 9.10 from cd, I can also upgrade from 9.04 to 9.10 through update manager

---

### Post by Leppie on 2010-01-12
well, that still would not explain why you're linux partition would be recognised as a swap partition.
to me it sounds like there is some issues with this drive, you may want to investigate some more (there's utilities out there to check the drive's integrity).

---

### Post by Leppie on 2010-01-12
i haven't been able to find anything on hardware not being compatible with the ext4 filesystem, but you could try creating an ext4 partition on the drive, copy some files to it and reboot to see if that is the problem.

---

### Post by hunterkasy on 2010-01-12
> **Leppie said:**
> i haven't been able to find anything on hardware not being compatible with the ext4 filesystem, but you could try creating an ext4 partition on the drive, copy some files to it and reboot to see if that is the problem.

when I installed the 9.04 version, I did a manual partition, (I did that so I could create a home partition) but I did use ext4 partition for root and home, and the install went just fine, I was able to boot into 9.04 and I did a upgrade to 9.10 through update manager and that went fine, now I am able to run 9.10 on that system, from a upgrade from 9.04,

---

