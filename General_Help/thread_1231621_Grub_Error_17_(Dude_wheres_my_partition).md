---
title: "Grub Error 17 (Dude wheres my partition?)"
date: 2009-08-04
forum: General Help
---

### Post by limptwiglet on 2009-08-04
Hi,

I have installed Ubuntu 9.04 64bit on my Clevo M860TU and after running an update and restarting I'm getting a Grub error 17 message.

I have poked around a bit on the forums and have found a few people with this problem but none seem to be quite what I'm suffering from.

So I stuck the live CD in and tried the following stuff but to no avail.

First thing I tried was "sudo fdisk -l":

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   82  Linux swap / Solaris
/dev/sda2             244       38913   310616775    5  Extended
/dev/sda5             244        3890    29294496   83  Linux
/dev/sda6            3891       38913   281322216   83  Linux
```

I then tried "sudo fdisk /dev/sda" which gave me this output:

```

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```

To me this dosnt seem to show any problems, perhaps I'm not looking in the right place.

I then tried "sudo gparted" which did show a problem. It showed that /dev/sda5 is an unknown format.

I'm sure this is because the partition Ubuntu is installed on is broken but I also tried using the grub command line tool to see if I could fix it that way to no avail.

Any help would be greatly appreciated.

Thanks

Mark

---

### Post by merlinus on 2009-08-04
Is linux / on sda5 or sda6?

Also, look in Places and click on your hdd, then navigate to /media/disk (or something like that, and then to /boot/grub/menu.lst.  Open it with the text editor by rightclicking and selecting that app, and post results.

Of course, if the partition that / is on is corrupted. nothing but a fresh install will do.

---

### Post by limptwiglet on 2009-08-04
Hi thanks for the reply

Yeah its on sda5, there is nothing on my hdd lost+found and mark.

If thats the case then I really need to move back to another OS, as I have re-installed 9.04 4 times now all with the same problems, I have also tried openSuse 11.1 and Fedora all with very similar problems.

---

### Post by merlinus on 2009-08-04
Try this:

```
sudo grub
root (hd0,4)
setup (hd0)
quit

```If no errors, restart.

---

### Post by limptwiglet on 2009-08-04
I get cannot mount partition

---

### Post by merlinus on 2009-08-04
Try this to force mount the partition:

```
sudo mkdir /media/disk
sudo mount -t ext3 /dev/sda5 /media/disk -o force
```

assuming it is formatted as ext3.

the o is a lowercase O

---

### Post by limptwiglet on 2009-08-06
Right im getting all sorts of funky errors now, and they appear to be different every time i boot. Sometimes it starts some times it dosnt.
Could this be due to ext4 file system, would ext3 be better or more stable?

---

### Post by merlinus on 2009-08-06
If formatted as ext4:

```
sudo mount -t ext4 /dev/sda5 /media/disk -o force
```There have been a number of reported problems with ext4 -- seemingly not stable at this point.

---

### Post by limptwiglet on 2009-08-07
I have re-installed with ext3, ill see how that goes. But so far so good.

---

### Post by limptwiglet on 2009-08-08
Woops broken again.

---

### Post by merlinus on 2009-08-08
You might try running fsck on the partition, but make sure it is unmounted.

---

### Post by louieb on 2009-08-08
Check your hard drive perhaps its about to die. Most drives made in the last 9 years have smart technology built in.  

Get a [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") it has a program called GsmartControl - this is a front end for smartmontools. Pretty nice program. Not in the repositories now but have heard it will be included in v9.10.   

> The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks. It is derived from the smartsuite package, and includes support
for ATA/ATAPI-5 disks. It should run on any modern Linux system.

---

### Post by limptwiglet on 2009-08-09
I highly doubt my hard drive is about to die as its not even 6 months old. Plus I had 9.10 running on it since launch, but i decided to try another distro, but then came back to Ubuntu to find this massive mess.

I'll try fsck now and see what happens.

Thanks

Mark

---

### Post by limptwiglet on 2009-08-09
Right I booted into Live CD and ran fsck and got a ton of errors. I just ran through them all hitting yes yes yest. It seems to be working again.
Ill see if it happens again, I have a feeling it will.

Thanks

Mark

---

### Post by merlinus on 2009-08-09
Glad fsck fixed the problems, atl least for now.  Be sure to back up important data regularly, however, lest something go wrong again.

As for the age of your hdd and failure, this happens all-too-often.  That's why there is usually a one-year warranty.  And some are DOA as well.

---

