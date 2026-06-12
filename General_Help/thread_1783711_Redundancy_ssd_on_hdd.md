---
title: "Redundancy ssd on hdd"
date: 2011-06-16
forum: General Help
---

### Post by atlante on 2011-06-16
Hi guys,
 I bought a brand new PC with 2 hard disk: a solid state 250gb and a 500gb sata drive. On the first one, I installed Ubuntu LTS 10.04.2.
 My question is: how can I make the redundancy of the boot partition and / on the sata disk?
 I thought to clone the internal hard disk and then run a rsync before every shutdown.
 But the PC doesn't always boot from the ssd and change the boot sequence from the bios has no effect.
 I had also considered the idea of &#8203;&#8203;a raid 1 with mdadm, but it seems to worsen the performance.
 Thanks in advance for your attention

---

### Post by dcstar on 2011-06-16
> **atlante said:**
> Hi guys,
 I bought a brand new PC with 2 hard disk: a solid state 250gb and a 500gb sata drive. On the first one, I installed Ubuntu LTS 10.04.2.
 My question is: how can I make the redundancy of the boot partition and / on the sata disk?
 I thought to clone the internal hard disk and then run a rsync before every shutdown.
 But the PC doesn't always boot from the ssd and change the boot sequence from the bios has no effect.
 I had also considered the idea of &#8203;&#8203;a raid 1 with mdadm, but it seems to worsen the performance.
 Thanks in advance for your attention

Boot off a Live CD/USB and install **gparted** to copy the boot partition to the other drive.

Don't forget to change the UUID of the copied partition otherwise it will be used if the UUID remains identical (search for detailed instructions).

---

### Post by atlante on 2011-06-16
> **dcstar said:**
> Boot off a Live CD/USB and install **gparted** to copy the boot partition to the other drive.

Don't forget to change the UUID of the copied partition otherwise it will be used if the UUID remains identical (search for detailed instructions).

ok. but if the ssd fail boot, will it boot from the sata hard disk? can you link me the instruction for change the uuid?

---

### Post by oldfred on 2011-06-16
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX


But I would just do another install on the SATA drive and copy /home. You should have some settings on the SSD that would not be best for the SATA drive & vice-vera.

I always do new/clean installs so my backup procedure is to make sure I have all the info I need to reinstall.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

If not ever planning on running windows you may want to consider gpt instead of MBR(msdos). But with gpt you cannot redo a UUID. The archlinux site recommends gpt for SSD drives.

---

### Post by srs5694 on 2011-06-16
> **oldfred said:**
> But with gpt you cannot redo a UUID.

Fortunately, you're mistaken about this:

```

$ **sudo parted /dev/sdb print | grep Table**
Partition Table: gpt
$ **sudo blkid /dev/sdb1**
/dev/sdb1: UUID="3d8e8390-c351-45e2-ada4-1b2afcf4ece3" SEC_TYPE="ext2" TYPE="ext3" 
$ **sudo blkid /dev/sdb1**
/dev/sdb1: UUID="7a46487d-11a0-4734-97b7-73778519316e" SEC_TYPE="ext2" TYPE="ext3" 

```

You might be getting confused because GPT assigns *G*UIDs, which are very similar to UUIDs, to partitions. Thus, any given partition will have a GUID and the filesystem it contains will have a UUID. The GUID and UUID will be different (unless you force them to be the same). Changing the UUID won't affect the GUID, and changing the GUID won't affect the UUID. AFAIK, Linux doesn't use the GUIDs for anything; you can't mount a partition by specifying its GUID, for instance.

---

### Post by oldfred on 2011-06-17
@srs5694
Thanks, I had mixed up the GUID & UUIDs, I thought with gpt they were the same.

---

### Post by dcstar on 2011-06-17
> **atlante said:**
> ok. but if the ssd fail boot, will it boot from the sata hard disk??

If you set up and install Grub on the second hard disk to boot that partition, yes. Your BIOS also has to use the second disk in its boot order.

---

