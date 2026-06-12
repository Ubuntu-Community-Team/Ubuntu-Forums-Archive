---
title: "Hard disk problems"
date: 2010-10-19
forum: General Help
---

### Post by jon.reeve on 2010-10-19
So I'm traveling and I took out my desktop's 500G 3.5" SATA drive and brought it along with me. I just bought a enclosure for it to make it readable through USB, but something isn't working. Nautilus recognizes a "Generic External" drive but doesn't (or can't mount anything. 

I ran dmesg | tail and I got: 

```
[  739.932145] usb 1-2: new high speed USB device using ehci_hcd and address 6
[  740.067756] scsi7 : usb-storage 1-2:1.0
[  741.069095] scsi 7:0:0:0: Direct-Access     Generic  External         1.08 PQ: 0 ANSI: 4
[  741.072112] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  741.095142] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

and so I tried to mount it manually using: 

```
sudo mkdir /media/Leviathan
sudo mount -t ext4 /dev/sdc /media/Leviathan

```
but I get: 

```
mount: no medium found on /dev/sdc

```

Gnome's disk utility reads "no media detected." 

Any number of things could be wrong here. I could have damaged my hard drive in transit, I could have bought a bum enclosure, or something else. Could anyone recommend some steps I could take to troubleshoot this, or some disk repair utilities?

---

### Post by Morbius1 on 2010-10-19
> sudo mount -t ext4 /dev/sdc /media/LeviathanYou mount a partition to a mount point. /dev/sdc refers not to a partition but to an entire physical device.

The line should look like this:
> sudo mount -t ext4 /dev/sdc1 /media/LeviathanReplace /dev/sdc1 with whatever partition on sdc you want to mount.

---

### Post by jon.reeve on 2010-10-20
But the problem is that it's not recognizing any partitions on the device: 

```
jon@jon-laptop:~$ sudo fdisk -l
[sudo] password for jon: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1ec9c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        6632    53271508+  83  Linux
/dev/sda3   *        6633        8636    16097130   af  HFS / HFS+
/dev/sda4            8637        9729     8779491+   5  Extended
/dev/sda5            8637        9607     7799526   83  Linux
/dev/sda6            9608        9729      979933+  82  Linux swap / Solaris
jon@jon-laptop:~$ sudo mount -t ext4 /dev/sdc1 /media/Leviathan
mount: special device /dev/sdc1 does not exist

```

---

### Post by linux-hack on 2010-10-20
Did you plugit in a windows environment ? If yes, you have to safely remove it so linux can mount it. And try may be a fsck on you HD.

---

### Post by jon.reeve on 2010-10-23
> **linux-hack said:**
> Did you plugit in a windows environment ? If yes, you have to safely remove it so linux can mount it. And try may be a fsck on you HD.

Fsck doesn't seem to work. That might be the issue--it was in fact plugged into a windows computer recently. Is there a way to fix it using only ubuntu, though? I don't have access to a windows computer at the moment.

---

### Post by SeijiSensei on 2010-10-23
sudo apt-get install ntfsprogs

Then "man ntfsfix" for details.

---

### Post by jon.reeve on 2010-10-24
> **SeijiSensei said:**
> sudo apt-get install ntfsprogs

Then "man ntfsfix" for details.

The only partition is an ext4 partition, though. Does ntfs tools for for ext4?

---

### Post by SeijiSensei on 2010-10-25
> **jon.reeve said:**
> The only partition is an ext4 partition, though. Does ntfs tools for for ext4?

Hmm.  Why was it connected to a Windows machine then?  There's no native ext4 driver for Windows.  Did you try to mount it in Windows using one of the older ext drivers?  That might be the culprit.

Otherwise if it's really an ext4 filesystem, a "sudo fsck /dev/sdc1" ought to fix whatever problems it has.  Did that really not help when you tried it before?  What does "sudo fdisk /dev/sdc" show?

---

### Post by jon.reeve on 2010-10-26
> **SeijiSensei said:**
> Hmm.  Why was it connected to a Windows machine then?  There's no native ext4 driver for Windows.  Did you try to mount it in Windows using one of the older ext drivers?  That might be the culprit.

Otherwise if it's really an ext4 filesystem, a "sudo fsck /dev/sdc1" ought to fix whatever problems it has.  Did that really not help when you tried it before?  What does "sudo fdisk /dev/sdc" show?

It was only connected to a Windows machine briefly, because the guy that sold me the HD enclosure wanted to show me that it worked. It didn't work, but I figured it was just because windows doesn't read ext4. 

It never mounted in Windows to begin with, since it's ext4. Running fsck didn't work because there was no recognized partition--i.e. no sdc1, only sdc. Fsck kept saying that there was no medium detected. 

Anyway I finally got it to work by taking the enclosure back to the shop where I bought it. It turns out the kid that install the HD in the enclosure didn't do it properly, which was the cause of the problem. It was really difficult for us to troubleshoot, however, since his windows machines couldn't read my ext4 partition. We eventually were able to test it using ext2read.exe for Windows, which can browse ext4 partitions. But man, was that a lot of work. 

So anyway, I guess what I learned from this is, if linux recognizes the drive (/dev/sdc) but not the partition (/dev/sdc1) when there is one, one possible reason might be that the HD is not properly attached to its enclosure.

---

