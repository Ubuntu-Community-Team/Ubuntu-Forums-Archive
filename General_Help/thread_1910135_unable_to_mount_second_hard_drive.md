---
title: "unable to mount second hard drive"
date: 2012-01-16
forum: General Help
---

### Post by Corvair on 2012-01-16
Unable to mount location

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Hello everyone,

I am trying to mount my second hard drive that I use for backup.

Does the above message mean anything to you and what can I do to correct this?

---

### Post by carl4926 on 2012-01-16
What does it show like in

```
sudo fdisk -l
```

---

### Post by Corvair on 2012-01-16
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ba93ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59326   476536063+  83  Linux
/dev/sda2           59327       60801    11847937+   5  Extended
/dev/sda5           59327       60801    11847906   82  Linux swap / Solaris
claude@claude-desktop:~$ 

here is what I get

---

### Post by ajgreeny on 2012-01-16
Presumably sda is your internal main hard disk, not the second one?

I expected to see sda and sdb.  Is this an internal HDD or a USB external backup disk, and was it attached when you ran the **sudo fdisk -l** command?

It looks as if the system is not seeing it at all, as far as I can make out. If it is a USB drive, are you sure the USB socket is OK?

---

### Post by carl4926 on 2012-01-16
> **ajgreeny said:**
> Presumably sda is your internal main hard disk, not the second one?

I expected to see sda and sdb.  Is this an internal HDD or a USB external backup disk, and was it attached when you ran the **sudo fdisk -l** command?

It looks as if the system is not seeing it at all, as far as I can make out. If it is a USB drive, are you sure the USB socket is OK?

In addition
What can you tell us about the HD?
As much info as you can..

---

### Post by Corvair on 2012-01-17
Hello again

My main disk is internal and also the new one
The main disk is /dev/sda1
ST3500630as as listed in the motherboard menu ext3 version

The new disk is also internal and I installed as an ext2 because the only options were ext2 or ext3.
WDC WD5000aakx-083ca ext2

Both are 500 Gb.

I have used the new disk mainly for backup. At times it would not show on my COMPUTER so I had to go to the motherboard program and reinitialize the WD disk and then it showed up on my COMPUTER and I could open it.

Now it is showing on my computer but it will not mount.

Yes it was attached when I did the sudo fdisk -l command

---

### Post by carl4926 on 2012-01-17
You may want to edit it in to /etc/fstab

I can't recall how 10.04 managed devices

It all sounds a bit flaky to me.

---

### Post by gsgleason on 2012-01-17
> **Corvair said:**
> Yes it was attached when I did the sudo fdisk -l command

Are you sure about that?  When you showed the output of 'sudo fdisk -l' it was not there.

---

### Post by Corvair on 2012-01-17
It is inside my computer and it has been connected for quite a while.

I checked again

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ba93ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59326   476536063+  83  Linux
/dev/sda2           59327       60801    11847937+   5  Extended
/dev/sda5           59327       60801    11847906   82  Linux swap / Solaris

I will check my internal connections in case something has gone loose.

---

### Post by Corvair on 2012-01-17
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


I get an alarm indication when attempting to mount the disk: 
Smart Status     Disk failure is imminent.

I bought this hark disk in September, it is still on warranty so I am going to take it back and have them check it out.

---

### Post by Corvair on 2012-01-17
I was finally able to mount the hard disk but it is very slow at opening files so I think there may be a problem with the hard disk from Western Digital Caviar blue. I am starting to doubts about their caviar. My original, a Seagate barracuda is still working without a snitch after 4 years.

---

### Post by Corvair on 2012-01-17
After doing a Smart Data Self Test here is the result

Self Assessment: failing
Overall Assessment : Disk Failure, Backup all data and replace the disk

Looks evident: back to the store for an exchange

---

### Post by Corvair on 2012-03-11
I now have a new hard drive and this is what I get. 
The hard drive does not show on "computer". This is what I get now on the terminal.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ba93ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59326   476536063+  83  Linux
/dev/sda2           59327       60801    11847937+   5  Extended
/dev/sda5           59327       60801    11847906   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
claude@claude-desktop:~$

---

