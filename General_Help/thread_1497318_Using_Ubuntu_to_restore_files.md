---
title: "Using Ubuntu to restore files?"
date: 2010-05-30
forum: General Help
---

### Post by iamjava on 2010-05-30
Hello everyone. :)
 
My friend's computer is giving him the blue screen of death (have to LOVE Vista), so I decided to help him. I am pretty sure that it's from a virus that corrupted Vista, but I could be wrong, it could be the hard drive that went corrupt. Being that it's a laptop, I am hoping it's just the OS.
 
Now, I have Ubuntu on a disc, and it runs very smoothly. (Didn't install it, just chose run on the disc.) However, I couldn't see the files on the computer. I was wondering if there is a way to get those files without installing Ubuntu, because I am planning on upgrading the computer to Windows 7, but using the Ubuntu disc was the only way I could actually get to the desktop.
 
So, I guess my question is: is there any way to get the files from the computer on the C drive without having to install Ubuntu.
 
Thanks. :)

---

### Post by dino99 on 2010-05-30
you need a real install:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

mountmanager: deal with partitions and devices rights
clamav: check for virus and malwares

more info with links below

---

### Post by bcbc on 2010-05-30
> **iamjava said:**
> Hello everyone. :)
 
My friend's computer is giving him the blue screen of death (have to LOVE Vista), so I decided to help him. I am pretty sure that it's from a virus that corrupted Vista, but I could be wrong, it could be the hard drive that went corrupt. Being that it's a laptop, I am hoping it's just the OS.
 
Now, I have Ubuntu on a disc, and it runs very smoothly. (Didn't install it, just chose run on the disc.) However, I couldn't see the files on the computer. I was wondering if there is a way to get those files without installing Ubuntu, because I am planning on upgrading the computer to Windows 7, but using the Ubuntu disc was the only way I could actually get to the desktop.
 
So, I guess my question is: is there any way to get the files from the computer on the C drive without having to install Ubuntu.
 
Thanks. :)
The hard drive partition(s) aren't mounted by default. You have to select it in the live CD environment, either from the Places menu or you could mount them manually.

If you can't mount the drive, then there is a tool that can recover data from a damaged drive. It's called photorec.
But first see if you can mount the hard drive - in which case, use an external usb to recover anything of value before trying anything else.

---

### Post by iamjava on 2010-05-30
> **bcbc said:**
> The hard drive partition(s) aren't mounted by default. You have to select it in the live CD environment, either from the Places menu or you could mount them manually.
 
If you can't mount the drive, then there is a tool that can recover data from a damaged drive. It's called photorec.
But first see if you can mount the hard drive - in which case, use an external usb to recover anything of value before trying anything else.
 
How do you mount it? I can't back up any files because I don't have access to them (Vista died and Ubuntu isn't giving me access ATM), thus why I am trying to use Ubuntu to get to them. :|

---

### Post by bcbc on 2010-05-30
> **iamjava said:**
> How do you mount it? I can't back up any files because I don't have access to them (Vista died and Ubuntu isn't giving me access ATM), thus why I am trying to use Ubuntu to get to them. :|

First I would try the Places menu, look for the drive and click on it. If that doesn't work, go to Applications, Accesories and click on Terminal.

Then type ```
sudo fdisk -l
``` and you'll see something like:
```
Disk /dev/sda: 120.1 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6635f736

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         479     3621208+   b  W95 FAT32
/dev/sda2   *         480       13847   101062080    7  HPFS/NTFS
/dev/sda3           13848       15508    12557160    5  Extended
/dev/sda5           13848       15431    11975008+  83  Linux
/dev/sda6           15432       15508      582088+  82  Linux swap / Solaris

```

In this case, my windows is on /dev/sda2 (the boot flag is a good clue as well as the size and the System type (NTFS).

Then you can mount it as follows:
```
sudo mount /dev/sda2 /mnt
```

Then, to view your files enter ```
nautilus /mnt
```

---

### Post by iamjava on 2010-05-30
> **bcbc said:**
> First I would try the Places menu, look for the drive and click on it. If that doesn't work, go to Applications, Accesories and click on Terminal.
 
Then type ```
sudo fdisk -l
``` and you'll see something like:
```
Disk /dev/sda: 120.1 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6635f736
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         479     3621208+   b  W95 FAT32
/dev/sda2   *         480       13847   101062080    7  HPFS/NTFS
/dev/sda3           13848       15508    12557160    5  Extended
/dev/sda5           13848       15431    11975008+  83  Linux
/dev/sda6           15432       15508      582088+  82  Linux swap / Solaris

```
 
In this case, my windows is on /dev/sda2 (the boot flag is a good clue as well as the size and the System type (NTFS).
 
Then you can mount it as follows:
```
sudo mount /dev/sda2 /mnt
```
 
Then, to view your files enter ```
nautilus /mnt
```
 
When typing in 'sudo fdisk -1', I get 'fdisk: invalid option -- '1'

---

### Post by bcbc on 2010-05-30
> **iamjava said:**
> When typing in 'sudo fdisk -1', I get 'fdisk: invalid option -- '1'

it's a lower case L (if in doubt cut and paste the command)

Edit: ```
l1  - actually this font is misleading since they look pretty much identical,
 but I guess the benefits of fixed spacing outweigh that
```

---

### Post by iamjava on 2010-05-30
> **bcbc said:**
> it's a lower case L (if in doubt cut and paste the command)
 
Edit: ```
l1  - actually this font is misleading since they look pretty much identical,
 but I guess the benefits of fixed spacing outweigh that
```
 
Ah, I see. I am not online with the other computer, so I can't copy and paste anything.
 
I think it is a hardware error.. I tried mounting the partition, but it came out with an Input/output error. If I installed, say, Windows 7, there are programs to recover files, right? (Assuming the installation actually works.)

---

### Post by bcbc on 2010-05-30
Try photorec.

From the live CD, first check if it's installed already. ```
photorec --help
```

If not it tells you how to install it ```
sudo apt-get install testdisk
```
(Note: you have to enable the universe repository if it isn't already (System, Aministration, Software sources, then on the first tab click on "Community maintained ... (Universe)").

Then to try and recover files enter (assuming you have an external USB mounted under /media/ExternalUSB and your windows is on /dev/sda2):
```
sudo photorec /d /media/ExternalUSB /dev/sda2
[Proceed]
[None]
[Search]
```

Edit: You can also search the entire drive (replace /dev/sda2 with /dev/sda) which is better if the partition table is messed - although it doesn't sound like it in this case).


Also see: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

NOTE: any files recovered have names like f12345678.jpg or f0000123.doc so you'll have to figure out what got saved later.

---

### Post by N8N on 2010-05-30
I was presented with this exact issue a while ago... the live CD is useless for this purpose, or if it's not, I was unable to figure out how to make it work.  I had the same problem; unable to mount anything, and if I did manage to mount something it wouldn't let me access any of the files on the drive.  Easiest workaround is to simply remove the old HDD from your friend's computer and connect it to a computer with a properly installed OS, I prefer Linux just because it will read everything while Windows will only read FAT and NTFS.  If you don't have a spare IDE or SATA connection, or if your friend's disk is IDE and you only have a SATA controller or vice versa, just get an inexpensive USB to IDE/SATA cable.  that little toy has saved my butt several times over the past few months.

good luck

nate

---

