---
title: "Help with mounting Seagate USB Pocket Drive"
date: 2006-04-01
forum: General Help
---

### Post by red devil on 2006-04-01
I'm running Ubuntu 5.10 and want to access a Seagate 5GB Pocket Drive via USB.
I've done a

> mkdir /mnt/usbdrive

then I added:

> /dev/usbdrive /mnt/usbdrive vfat user 0 0

to my Fstab.
When I plug in the drive and enter 

> mount /mnt/usbdrive

I get the following reply

> mount: special device /dev/usbdrive does not exist


What am I doing wrong/missing?
Thanks guys.

---

### Post by Ramses de Norre on 2006-04-01
>  mount /mnt/usbdrive
You're mounting the mount point instead of the device.

Do dmesg|tail in terminal after plugging in the drive to see the device code (you assumed it was /dev/usbdrive? that sounds like not correct to me..) and try mounting that, you'll need to set the correct code in fstab too.

---

### Post by Sutekh on 2006-04-01
You can't mount /dev/usbdrive.  You need to determine the location of the USB and substitute that instead

```
sudo fdisk -l
```Will let you know the location; /dev/sda1 or /dev/sdc1, etc, etc.

Then you can add this line to the fstab
```
/dev/**sda1**   /mnt/usbdrive   vfat   iocharset=utf8,umask=0000   0   0
```
Changing sda1 with what is appropriate for your USB drive

Then use
```
sudo mount -a
```
to remount the partitions in the fstab without rebooting.

---

### Post by red devil on 2006-04-01
Thanks for the quick replies... and don't I feel an idito trying to a) mount the mount folder and b) forgetting to list the device as sda1!
I can now see the Seagate icon in 'Computer' but when I try to mount it with the right-click 'Mount Volume' command I get the following message:

> mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error

I thought Vfat was the correct file system type... any suggestions?
Thanks

---

### Post by Sutekh on 2006-04-01
You can be sure of the filesystem from the output of fdisk.  What did it say?

---

### Post by red devil on 2006-04-01
It said: 

> sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9777    78533721   83  Linux
/dev/hda2            9778        9964     1502077+   5  Extended
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/sda: 5000 MB, 5000970240 bytes
255 heads, 63 sectors/track, 608 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+   b  W95 FAT32


So that, to me, looks like a FAT32 file system?? Will that work in Linux?

---

### Post by Sutekh on 2006-04-01
Yep thats FAT32 alright.  Okay try that mounting line but without the **iocharset=utf8**
```
/dev/sda1   /deb/usbdrive   vfat   umask=0000   0   0
```

---

### Post by red devil on 2006-04-01
Nope, removed that part in Fstab but got the same error message as before... do you have any other suggestions please? What if I made the file system FAT32 in Fstab?

PS Sutekh... I notice in your suggested example you've included /deb/usbdrive (which I assume is /dev/usbdrive) - shouldn't that be /mnt/usbdrive or does Ubuntu handle mounting differently to other distros ie it puts the mount command in /dev?

---

### Post by Sutekh on 2006-04-01
Unfortunately FAT32 isn't a recognised option that can go in the fstab.  VFAT is the right one.  Did you partition the drive yourself?  I'm trying to rule out whether it really is formatted FAT32.  

Also try mounting the partitions with ```
sudo mount -a
```rather than right-clicking and choosing 'Mount Volume'.  That method does not use the entry in the fstab.

---

### Post by red devil on 2006-04-01
Nope again, I'm afraid...

> sudo mount -a

still returns the same error about the filesystem when I attempt to open the drive in a separate Nautilus window.
I've never physically partitioned the drive - it started out as a Windows USB drive but since then - and I'm talking a year or so - has been used on many different Linux distros with no problems.
It has all my MP3/Ogg Vorbis collection on it so I'm anxious not to have to wipe it clean and repartition it.

PS Interestingly, I've just plugged the drive into my other machine which has a vanilla Frugalware 0.4 install running KDE 3.5 on it, and it was immediately detected and Konqueror opened up a window so I could access it.
I ran fdisk -l in Konsole just to check, and it gives the same results as I got in Ubuntu... a FAT32 filesystem... weird!

---

### Post by red devil on 2006-04-01
I suppose I could copy all my music off the drive in my Frugalware machine, then reformat it into a filesystem that Ubuntu would recognise? Do you know how I could do that?
Cheers

---

### Post by Ramses de Norre on 2006-04-01
The reformating? Use gparted, it's in the repo's.

---

### Post by red devil on 2006-04-01
Hi,
Managed to fix this.
Firstly, I copied everything off the drive onto my other machine, so nothing's lost by what followed.
Apt-get installed gparted, then used it to convert filesystem on Pocket Drive from FAT32 to Ext 3, then changed fstab to read as follows:

> /dev/sda1   /mnt/usbdrive   ext3    user,auto   0   0


The result being that when the drive is plugged in, it is auto-mounted and Nautilus opens so I can browse the drive.
Thanks for the help guys - much appreciated.

---

### Post by Sutekh on 2006-04-01
Sweet!  That's great.  I'm sure if you re-formatted it with FAT32 it would have worked, it must have been some kind of formatting error I guess.  Doesn't matter now.  

Double thumbs up for using ext3 too ;)

---

