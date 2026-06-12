---
title: "Mounting SATA drive."
date: 2010-04-29
forum: General Help
---

### Post by HHx66 on 2010-04-29
I'm trying to mount my SATA drive that has Windows on it under Xubuntu, it's NTFS formatted, I tried adding it to fstab, I know the /dev points are right I checked with sudo lshw -C disk
and with fdisk -l, the drive is partitioned 3 ways 1 for Win7, one for Win7's system info partition or whatever, and 1 for documents, but when I try mounting with mount -a with /dev/sda1 (which is where the windows partition should be) I get this:

```
Error opening '/dev/sda1': No such device or address
Failed to mount '/dev/sda1': No such device or address
Either the device is missing or it's powered down, or you have
SoftRAID hardware and must use an activated, different device under
/dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1) to mount NTFS.
Please see the 'dmraid' documentation for help.

```

---

### Post by HHx66 on 2010-04-29
I am running this disk as a JBOD on a nForce 3 SATA chipset, any help on this?

---

### Post by limey_rick on 2010-04-29
If it was a JBOD, then it was effectively part of a RAID pair? Do you have a onboard RAID controller in the MB? 

Its possible that the disk has some header information on it that identifies it as a RAID disk, so Linux won't be able to mount it as an NTFS disk. You may have to mount it as a FakeRaid disk using DMRAID.

[https://wiki.ubuntu.com/DmraidSupport](https://wiki.ubuntu.com/DmraidSupport)

---

### Post by HHx66 on 2010-04-29
Thats what I had to do, its actually only one SATA hard disk, but the options for SATA are either RAID1/0 on or if thats off its JBOD no matter what, I don't what for. But basically I ended up having to do:

```
sudo dmriad -ay
```

which gave me the /dev/mapper names of the partition and activated, and then allowed me to mount it like any other drive.

---

