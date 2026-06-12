---
title: "Digi box"
date: 2012-03-18
forum: General Help
---

### Post by chuggly on 2012-03-18
Hello all,

I have an 'ONN' digi box bought from Asda which has died.

It contains a 160GB 3.5" hdd & I have an adapter to connect the usb of my laptop running Ubuntu 11.10 to the hdd. 

The hdd is partitioned in 2 & I can access the first partition 214mb.

When trying to access the 2nd partition, where all the recordings are, I get an error:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The o/p of dmesg | tail is

 dmesg | tail
[   22.199034] cfg80211: Regulatory domain changed to country: DE
[   22.199036] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.199039] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199041] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199044] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199046] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   22.410239] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.910664] EXT2-fs (sdb2): error: bad blocksize 32768
[   32.848052] wlan0: no IPv6 routers present
[  520.224870] EXT2-fs (sdb2): error: bad blocksize 32768

My question is is there any way I can mount the drive & retrieve the recordings

Many thanks

Tim

---

### Post by plucky on 2012-03-18
> **chuggly said:**
> Hello all,

I have an 'ONN' digi box bought from Asda which has died.

It contains a 160GB 3.5" hdd & I have an adapter to connect the usb of my laptop running Ubuntu 11.10 to the hdd. 

The hdd is partitioned in 2 & I can access the first partition 214mb.

When trying to access the 2nd partition, where all the recordings are, I get an error:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The o/p of dmesg | tail is

 dmesg | tail
[   22.199034] cfg80211: Regulatory domain changed to country: DE
[   22.199036] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.199039] cfg80211:     (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199041] cfg80211:     (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199044] cfg80211:     (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.199046] cfg80211:     (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   22.410239] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.910664] EXT2-fs (sdb2): error: bad blocksize 32768
[   32.848052] wlan0: no IPv6 routers present
[  520.224870] EXT2-fs (sdb2): error: bad blocksize 32768

My question is is there any way I can mount the drive & retrieve the recordings

Many thanks

Tim


What does **sudo fdisk -l** show you when the drive is connected?

Could be the partition is corrupt or dirty and possibly needs to be cleaned.

What does gParted see as the file system on the drive?

---

### Post by Zill on 2012-03-18
> **chuggly said:**
> ...My question is is there any way I can mount the drive & retrieve the recordings.
I will leave others to determine if this is technically possible.  However, I would ask what you intend to do with any retrieved recordings?

My understanding is that Freeview DVB recordings are saved in a compressed format that can only be played back via a Freeview DVB box.  i.e they cannot simply be played via a standard PC media player such as VLC.

You *may* have some success if you can transfer the retrieved recordings to a new HDD that has previously been formatted in a DVB recorder.

Caveat:  Although I have successfully replaced a DVB HDD with a different HDD previously used in a PC I have never tried to transfer any programs.

---

### Post by chuggly on 2012-03-18
Thanks for the replies.

Plucky

Sudo fdisk -l shows

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2086

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   152129535    76063744   83  Linux
/dev/sda2       152131582   156301311     2084865    5  Extended
/dev/sda5       152131584   156301311     2084864   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      417689      208813+  83  Linux
/dev/sdb2          417690   312576704   156079507+  83  Linux

Gparted
/dev/sdb2 has an exclamation mark . Its format is ext2, but if I look at the device information it says
Partition table msdos
Heads 255
Sectors/track 63
Cylinders 19457
Total sectors 312581808
Sector size 512

The thing that looks odd tho me, is the disk identifier is 0x00000000.
I thought this was a hex/dec number

Zill

I want to watch the recordings if possible. If this is not possible, I'll format the disk, get a caddy & have another portable HDD.

There is no chance of replacing the HDD as the machine itself is dead.

I did wonder about the format.

Thanks again

Tim

---

### Post by Zill on 2012-03-18
> **chuggly said:**
> ...I want to watch the recordings if possible. If this is not possible, I'll format the disk, get a caddy & have another portable HDD...
If you are *really* keen on watching the recordings on your PC then this Digital Spy thread might help...
[Goodmans GHD8015F2 (Vestel) Recording Extraction]("http://forums.digitalspy.co.uk/showthread.php?t=992467")

AIUI, your ONN PVR will be a [Vestel clone]("http://www.vestelpvr.futaura.co.uk/"), as the Goodmans and so many others are. ;-)

If you go ahead with this task, it would be good if you could report the outcome back here to help others in future.  Good luck!

---

### Post by chuggly on 2012-03-22
Thanks Zill

I'll give it a go.

Sorry for the delay, I work away during the week.

Regards

Tim

---

