---
title: "WARNING: Not enough clusters for a 32 bit FAT!"
date: 2010-06-23
forum: General Help
---

### Post by Tumex on 2010-06-23
Hey there guys,
Whenever I try to format my 2.0GB USB stick, I get the following error:

```

Error formatting volume

Error creating file system: helper exited with exit code 1: helper failed with:
WARNING: Not enough clusters for a 32 bit FAT!
mkfs.vfat: Attempting to create a too large file system

mkfs.vfat 3.0.7 (24 Dec 2009)

```

I was hoping somebody could help me! Thanks. :)

---

### Post by MooPi on 2010-06-23
What tool are you using to format the stick with? What file format was previously on the stick?

---

### Post by Tumex on 2010-06-23
> **MooPi said:**
> What tool are you using to format the stick with? What file format was previously on the stick?
I use Disk Utility and the file format is FAT (32-bit version).

I tried through the command line as well, but to no avail!

---

### Post by MooPi on 2010-06-23
Install gparted through synaptic.
It is a better tool than disk utility. Try to remove the partition first before the format then add new partition to the empty space to see if that works.

---

### Post by Tumex on 2010-06-23
> **MooPi said:**
> Install gparted through synaptic.
It is a better tool than disk utility. Try to remove the partition first before the format then add new partition to the empty space to see if that works.
For some reason I cannot see my USB stick in gparted, but can see it clearly in Disk Utility. I only get dev/sda/ which is my HDD, but no dev/sdc which is my stick!

---

### Post by CharlesA on 2010-06-23
What does this return?

```
sudo fdisk -l
```

---

### Post by Tumex on 2010-06-23
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc8bfc8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26108   209712478+   7  HPFS/NTFS
/dev/sda2           26109      121600   767039459+   f  W95 Ext'd (LBA)
/dev/sda5           26109      102019   609753058+   7  HPFS/NTFS
/dev/sda6          102020      121339   155187868+  83  Linux
/dev/sda7          121340      121600     2096451   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdc: 2017 MB, 2017984512 bytes
63 heads, 62 sectors/track, 126 cylinders
Units = cylinders of 3906 * 4096 = 15998976 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

At the very end, I noticed this:
Disk /dev/sdc doesn't contain a valid partition table

Mm? :o

---

### Post by CharlesA on 2010-06-23
That might be why gparted is having a problem, but I don't know for sure.

Delete the partition and then create it again, if you can.

---

### Post by Tumex on 2010-06-23
> **CharlesA said:**
> That might be why gparted is having a problem, but I don't know for sure.

Delete the partition and then create it again, if you can.
How would I go about deleting the partition if gparted doesn't detect it? Thanks for the help till now. ;)

---

### Post by CharlesA on 2010-06-23
> **Tumex said:**
> How would I go about deleting the partition if gparted doesn't detect it? Thanks for the help till now. ;)

I think you can use fdisk to delete the partitions. Check [here]("http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/").

---

### Post by dino99 on 2010-06-23
> **Tumex said:**
> How would I go about deleting the partition if gparted doesn't detect it? Thanks for the help till now. ;)

fat32 formatting is better done with windows tools, or partedmagic into linux [http://partedmagic.com/](http://partedmagic.com/)

to deal with partitions and devices, install mountmanager, and set your prefs (system admin mountmanager)

pmount and usbmount have to be installed too (see into synaptic)

---

### Post by dcstar on 2010-06-24
> **Tumex said:**
> [code]
........
At the very end, I noticed this:
Disk /dev/sdc doesn't contain a valid partition table


Use **dd** to wipe the whole device, and if you still cannot use gparted to write a new Partition Table after that then you may well have a faulty USB device.

---

### Post by runesvend on 2010-09-27
> **Tumex said:**
> ```
[snip ...]
**Note: sector size is 4096 (not 512)**

Disk /dev/sdc: 2017 MB, 2017984512 bytes
63 heads, 62 sectors/track, 126 cylinders
Units = cylinders of 3906 * 4096 = 15998976 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): **4096 bytes / 4096 bytes**
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

At the very end, I noticed this:
Disk /dev/sdc doesn't contain a valid partition table

Mm? :o
You're having problems because your USB stick uses a sector size of 4096 bytes instead of the usual 512 bytes. gparted doesn't support this very well. fdisk does, however. Here's how you get the disk up and running:

Start up fdisk on your USB stick (remember to replace the */dev/sdc* part with the device name of your USB stick, if this has changed since the above output was produced):

```
sudo fdisk -cu /dev/sdc
```

Create a new DOS partition table by typing in an 'o' and pressing enter. Now write this partition table to the disk by typing 'w' and pressing enter. fdisk will write the partition table and exit.

Now we'd like to create a partition on that USB stick, so fire up fdisk again on the device as you did before:

```
sudo fdisk -cu /dev/sdc
```

Type in an 'n' and press enter to start. We want to create a primary partition, so type in a 'p' and confirm that by pressing enter. Now it asks for a partition number; how about entering '1' as the partition number, this seems suitable for the first partition. Press enter.
Press enter again to confirm the suggested first sector number, and once again to accept the suggested the last sector number.
Now type in a 'w' and press enter to write what we've just specified to the disk.

Now let's create that file system that we've all been waiting for. I'm not sure if this "Not enough clusters..."-warning is relevant, but assuming it is, we'll create a 16 bit FAT file system on the disk instead.

First we need to know how many sectors are on your USB stick. To do this we use fdisk this way:

```
sudo fdisk -cul /dev/sdd
```

You'll see some output like this at the end:

```
...

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             512      521087     **1041152**   83  Linux

```

The important part here is how many blocks are on the device (in bold). Copy this number so you're ready to paste it for the next and final command.

Now we'll create a 16 bit FAT file system on the disk that fills out the partition on the drive:

```
sudo mkfs.vfat /dev/sdc1 -F 16 -S 4096 <blocks>
```

Just change the <blocks> part to the number of blocks you got from the fdisk command immediately above.

You should be good to go!

---

