---
title: "How to make a 64 bit UUID"
date: 2010-05-03
forum: General Help
---

### Post by quadproc on 2010-05-03
While preparing to rearrange partitions and to remove Windows I noticed that my new disk drive lacks a device UUID.  The other disks in this system both have 64 bit UUIDs assigned to the disk's first partition (e.g., sda1 and sdc1) but the disk of interest (sdb) does not.  Disk sdb does have UUIDs assigned to its extended partitions.  I don't know how it ended up in this state; the only thing that I did with sdb was to use gparted to partition it and install ext3 and swap partitions.  Here is the output of blkid:
```
sudo blkid
/dev/sda1: UUID="26AE4A30AE49F937" TYPE="ntfs" 
/dev/sda5: UUID="b92fb3a5-c503-4168-a61f-7e6ea6661a0a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="b0b35cc7-895a-456e-8a3c-af1fd8457a7e" TYPE="swap" 
/dev/sda7: UUID="df533fe8-68c3-41f6-b030-e955feb580d9" TYPE="ext3" 
/dev/sda8: UUID="b071f4d5-5384-4267-9f78-99e163d6ea4a" TYPE="swap" 
/dev/sdc1: UUID="F4EE44F4EE44B122" TYPE="ntfs" 
/dev/sdb5: UUID="ae2cdad8-459c-4692-908d-eea07cd1fe9b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="a7d2d1fc-dd54-4226-b4fd-f9c145f319a4" TYPE="swap" 
```(Note: I plan to convert sdc to an Ubuntu data disk with one partition and a good filesystem at the present time.)

The uuidgen program works fine to produce a 128 bit UUID but I can't find any way to make it produce a 64 bit (or less) UUID.

Does anyone know how to generate legitimate 64 bit UUIDs?  Thanks.

quadproc

---

### Post by perham on 2010-05-03
> **quadproc said:**
> While preparing to rearrange partitions and to remove Windows I noticed that my new disk drive lacks a device UUID.  The other disks in this system both have 64 bit UUIDs assigned to the disk's first partition (e.g., sda1 and sdc1) but the disk of interest (sdb) does not.  Disk sdb does have UUIDs assigned to its extended partitions.  I don't know how it ended up in this state; the only thing that I did with sdb was to use gparted to partition it and install ext3 and swap partitions.  Here is the output of blkid:
```
sudo blkid
/dev/sda1: UUID="26AE4A30AE49F937" TYPE="ntfs" 
/dev/sda5: UUID="b92fb3a5-c503-4168-a61f-7e6ea6661a0a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="b0b35cc7-895a-456e-8a3c-af1fd8457a7e" TYPE="swap" 
/dev/sda7: UUID="df533fe8-68c3-41f6-b030-e955feb580d9" TYPE="ext3" 
/dev/sda8: UUID="b071f4d5-5384-4267-9f78-99e163d6ea4a" TYPE="swap" 
/dev/sdc1: UUID="F4EE44F4EE44B122" TYPE="ntfs" 
/dev/sdb5: UUID="ae2cdad8-459c-4692-908d-eea07cd1fe9b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="a7d2d1fc-dd54-4226-b4fd-f9c145f319a4" TYPE="swap" 
```(Note: I plan to convert sdc to an Ubuntu data disk with one partition and a good filesystem at the present time.)

The uuidgen program works fine to produce a 128 bit UUID but I can't find any way to make it produce a 64 bit (or less) UUID.

Does anyone know how to generate legitimate 64 bit UUIDs?  Thanks.

quadproc

please post the output of :

```
sudo fdisk -l
```

---

### Post by quadproc on 2010-05-03
> **perham said:**
> please post the output of :

```
sudo fdisk -l
```
Here it is:
```
sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb46582ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17719   142326843+   7  HPFS/NTFS
/dev/sda2           17720      121601   834432165    5  Extended
/dev/sda5           17720       39603   175783198+  83  Linux
/dev/sda6          120470      121601     9092758+  82  Linux swap / Solaris
/dev/sda7           39604      118240   631651671   83  Linux
/dev/sda8          118241      120469    17904411   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb46582be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18242   146521088    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4931

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      101448   814881028+   5  Extended
/dev/sdb5               1       76794   616847742   83  Linux
/dev/sdb6           76795       78970    17478688+  82  Linux swap / Solaris

```

I am not sure that fdisk works correctly on disks this large but what you see above is what fdisk says.

quadproc

---

### Post by WorMzy on 2010-05-03
I'm not sure what the problem is, but you seem to think you can mount a whole disk, rather than the partitions on the disk? Or are you trying to mount the extended partition? AFAIK you cannot mount disks or extended partitions, only partitions with a filesystem.

---

### Post by quadproc on 2010-05-03
> **WorMzy said:**
> I'm not sure what the problem is, but you seem to think you can mount a whole disk, rather than the partitions on the disk? Or are you trying to mount the extended partition? AFAIK you cannot mount disks or extended partitions, only partitions with a filesystem.
The problem is not related to mounting.  I am trying to assign a UUID to the first of the four partitions of the device and I have been unable to figure out how to produce a 64 bit UUID like the ones for sda1 and sdc1.  Once I can produce a suitable UUID then installing it should be trivial.

quadproc

---

### Post by perham on 2010-05-03
exactly as wormzy said.

there are two partitions on /dev/sdb which both have uuids that you provided in the initial post. there's nothing wrong there.

---

### Post by WorMzy on 2010-05-03
I think I'm beginning to understand. You're wondering where sdb2,3, and 4 are, correct? They don't exist, just like sda3 and 4 don't. Presumably they existed  at one point, but you have since replaced those partitions with new ones.

Anyway, if you're not looking to mount these partitions, it begs the question as to why you want these partitions to have UUIDs in the first place..?

---

### Post by quadproc on 2010-05-03
> **perham said:**
> exactly as wormzy said.

there are two partitions on /dev/sdb which both have uuids that you provided in the initial post. there's nothing wrong there.
Correct.  The thing that is missing is the UUID for sdb1.

quadproc

---

### Post by John Bean on 2010-05-03
> **quadproc said:**
> Correct.  The thing that is missing is the UUID for sdb1.

quadproc

It's not a data partition, it's an extended partition; of course it has no UUID.

There are only two data partitions on sdb and they both have UUIDs.

---

### Post by srs5694 on 2010-05-03
Some basics:

[UUID = Universally Unique Identifier](http://en.wikipedia.org/wiki/Uuid)
[GUID = Globally Unique Identifiers](http://en.wikipedia.org/wiki/Guid)

UUIDs and GUIDs are essentially the same thing. Both are 128-bit (32-byte) numbers. There's no such thing as a "64-bit UUID." There are, however, different ways to represent UUIDs/GUIDs (see the above-referenced Wikipedia articles for details). I don't know offhand why blkid is reporting 16-character (possibly 16-byte hexadecimal) values as "UUIDs" for your NTFS partitions. I'd speculate that these values are NTFS identifiers that are not technically UUIDs, but that are the closest thing to UUIDs that NTFS has. (I just don't know enough about NTFS to know if this is a possibility.)

UUIDs/GUIDs are used as a way to uniquely identify something, as their names imply. In disks, they're commonly used in three ways:


[list]
[*]An entire disk has a GUID when it's partitioned using the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) system. Most disks don't yet use GPT, though, and yours clearly don't, so this use of GUIDs is irrelevant in your case. [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_Boot_Record) disks, such as yours, have non-GUID identifiers (see the "Disk identifier" lines in your output).
[*]Every disk partition on a GPT disk has a GUID; however, as your disks don't use GPT, your partitions don't have GUIDs. There's nothing even remotely close to a partition GUID value in the MBR scheme.
[*]*Some* filesystems and other data structures employ UUIDs/GUIDs to identify particular filesystems. This is true of most Linux-native filesystems and of Linux swap space. I don't know if it's true of NTFS, but as I speculated above, I think it's likely that NTFS uses a non-UUID/GUID identifier. I'm pretty sure that FAT also uses a non-UUID/GUID identifier. Note that a filesystem is not the same as a partition; a filesystem can exist independent of a partition (as in an image file or a filesystem on an unpartitioned medium), and a partition can have no filesystem.
[/list]


As John Bean says, your /dev/sdb1 is an extended partition. As such, it contains no filesystem of its own; it's a placeholder for logical partitions. Therefore, /dev/sdb1 cannot have a UUID/GUID. Any tool you might use to assign a UUID/GUID to /dev/sdb1 would either refuse to do anything or would trash data in the partition, which might have the effect of rendering both the logical partitions in /dev/sdb1 inaccessible. (If you were very very lucky, an attempt to assign a UUID/GUID to /dev/sdb1 might do no obvious harm, since it might write to sectors that aren't in use.)

My only question is: Why did you think you needed to assign UUIDs to all your partitions? I'm not asking this rhetorically; I really want to know what led you so far astray in your understanding. If there's some badly written documentation out there, for instance, I'd like to know about it. (I'm the author of a GPT partitioning tool and I have Web pages on GPT, so I like to keep an eye on such things.)

---

### Post by quadproc on 2010-05-03
> **srs5694 said:**
> Some basics:

[UUID = Universally Unique Identifier]("http://en.wikipedia.org/wiki/Uuid")
[GUID = Globally Unique Identifiers]("http://en.wikipedia.org/wiki/Guid")

UUIDs and GUIDs are essentially the same thing. Both are 128-bit (32-byte) numbers. There's no such thing as a "64-bit UUID." There are, however, different ways to represent UUIDs/GUIDs (see the above-referenced Wikipedia articles for details). I don't know offhand why blkid is reporting 16-character (possibly 16-byte hexadecimal) values as "UUIDs" for your NTFS partitions. I'd speculate that these values are NTFS identifiers that are not technically UUIDs, but that are the closest thing to UUIDs that NTFS has. (I just don't know enough about NTFS to know if this is a possibility.)

Thank you for an informed and useful reply.

You asked how/why I was looking for a 64 bit UUID: that is a result of my looking at the data from blkid and observing that some devices are reported as having UUIDs which are less than 128 bits (and which are expressed in different formats that don't use dash separators within the numbers).

Incidentally, I have noticed that USB flash drives are reported by blkid as having 32 bit UUIDs but that these have a dash between two sets of 4 hex characters.

Since we computer users are more or less being forced to use UUIDs I believed that I would require one for each partition on sdb.  Since the new disk did not report one, I figured that I would need to add one.


All of this business is tangentially related to a bigger question which you might be able to help with: I would ultimately like to run RAID1 with the disks which are presently known as sda and sdb.  My mother board claims that hardware RAID1 is available by selecting suitable options in the BIOS but the documentation is very meager and I do not trust it.  It seems like I should be able to enable RAID1 without losing data but every article that I have seen says that repartitioning is necessary to enable RAID so data would be lost.  Why wouldn't RAID be able to "resurrect" the new blank disk when it was installed, as though it were a replacement for a failed disk?

Thanks for your help.

quadproc

---

### Post by srs5694 on 2010-05-03
> **quadproc said:**
> All of this business is tangentially related to a bigger question which you might be able to help with: I would ultimately like to run RAID1 with the disks which are presently known as sda and sdb.  My mother board claims that hardware RAID1 is available by selecting suitable options in the BIOS but the documentation is very meager and I do not trust it.  It seems like I should be able to enable RAID1 without losing data but every article that I have seen says that repartitioning is necessary to enable RAID so data would be lost.  Why wouldn't RAID be able to "resurrect" the new blank disk when it was installed, as though it were a replacement for a failed disk?

RAID can be implemented in hardware (the controller takes two or more disks and makes them look like one disk to the OS) or in software (the controller presents two or more disks as such and the OS combines them into whatever RAID level is configured). The last I heard, most on-motherboard RAID solutions don't provide true full hardware RAID; they just provide a few "hooks" and OS-level drivers do the rest -- this is something that's in-between the hardware and software RAID configurations. Unfortunately, drivers for Linux to use such configurations don't always exist. Thus, you may not be able to use the claimed RAID features, although you can use *any* hardware in a Linux software RAID configuration. I'm afraid I can't help you determine which you've got; you'll just have to research your own hardware in more detail.

---

### Post by quadproc on 2010-05-04
> **srs5694 said:**
> ... Thus, you may not be able to use the claimed RAID features, although you can use *any* hardware in a Linux software RAID configuration. I'm afraid I can't help you determine which you've got; you'll just have to research your own hardware in more detail.
I am afraid that I can't get any manufacturer's help on the RAID issue - the motherboard is an ASUS P6T SE and the manual that comes with it just briefly mentions RAID: it says enter BIOS setup during POST, select storage configuration, configure SATA as RAID, save changes and exit BIOS setup.  There is one other manual section where they define RAID 0, 1, 5, and 10.  And that is it.  A telephone call to their U.S. office elicited the paraphrased response "huh?".  Obviously I was unable to speak with anyone who knew anything relevant.

So, since I can't find out the ramifications or even the specs of their RAID I guess that I will have to either use fakeraid or none at all.

Thanks for everyone's help.  I am now making some progress on my configuration changes so I will mark this thread as solved.

quadproc

---

