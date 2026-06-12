---
title: "640 GB external HD not recognized correctly. Gparted problem?"
date: 2010-03-12
forum: General Help
---

### Post by leoh on 2010-03-12
I bough a 640 GB external USB disk.
I found something wasn't working well when I couldn't restore a backup from the disk (with sbackup).
So I tried to convert the filesystem from fat32 to something newer.
I installed gparted, and it shows no partitions on the 640 drive (however, I can access the filesystem!!!). Also, for some reason it shows as a 298.08 GiB drive.
So I thought I should format it to solve this. When I tried to do this, gparted simply closed, with no error messages.

So... is this an partition problem? GParted problem? Both?

---

### Post by coffeecat on 2010-03-12
It could be an error in the partition table. If so, simply reformatting the existing partition won't solve this.

In Gparted, go to Device > Create Partition Table. After you click on 'apply' for this you'll have a completely unallocated drive. Now create whatever partitions you want and see if this fixes the problem.

---

### Post by srs5694 on 2010-03-12
It's not clear to me precisely what's going on, but I have some hypotheses. One hypothesis is that you mistakenly accessed the wrong disk with GParted. If you happen to have an internal ~320GB drive, this explains the size discrepancy. (Disk manufacturers define KB, MB, GB, and TB differently than do most software programs, so a "320GB" hard disk will show up as being just under "300GB" in most disk utilities.) If this is true and if GParted actually made any changes to your 320GB disk before it closed/crashed, then ***do not shut down or reboot!*** Your partition table may be lost, and it will be much easier to recover now than after you shut down. (I doubt if your partition table is actually lost, but recovering can be very tough if it is.) Try typing "fdisk -l" as root (or via sudo) at a shell prompt to see what partitions are defined on all your disks. Alternatively, launch GParted again to view your partitions with its GUI. If you don't see partitions on your 320GB drive, then get help immediately. I won't go into more detail just yet, since chances are this isn't actually a problem, and details will be long and messy.

More generally, I think you should post the output of an "fdisk -l" run so we can see what is or isn't set up on your disk. Also, how were you mounting the contents of that disk before you decided to convert it from FAT? How did you set the disk up in the first place? My suspicion is that you were using it as a "superfloppy" -- that is, unpartitioned. This is legal, but potentially confusing. If I'm right, and if you don't mind losing anything stored on the drive, then you can use GParted, fdisk, or various other tools to create a fresh partition table (aka "disklabel") on the disk. In GParted, you first select the correct device (from the GParted->Devices menu) and then select the Device->Create Partition Table option. Be *sure* you're working on the correct device before you do this! You can then create partitions (Partition->New; you may need to click the unallocated space in the display first). If you use fdisk, you launch the program on the disk ("fdisk /dev/sdb" from a shell prompt, although you may need to change the device identifier). When you create a partition via 'n' and then save the changes by typing 'w', it'll create a new partition table. If you use fdisk, you'll then need to create a filesystem with the mkfs utility or something similar.

---

### Post by leoh on 2010-03-12
> **srs5694 said:**
> One hypothesis is that you mistakenly accessed the wrong disk with GParted.
Nope. The system has a 120 GB drive (which appears fine with the right partitions) and another external 640 GB drive with the problem.

> **srs5694 said:**
> More generally, I think you should post the output of an "fdisk -l" run so we can see what is or isn't set up on your disk.

```
Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x242d7a16

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10270    82493743+   7  HPFS/NTFS
/dev/sda2           13683       14593     7317607+   7  HPFS/NTFS
/dev/sda3           10271       13682    27406890    5  Extendida
/dev/sda5           10271       13535    26226081   83  Linux
/dev/sda6           13536       13682     1180746   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco
Nota: el tamaño del sector es 1024 (no 512)

Disco /dev/sdb: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 38912 cilindros
Unidades = cilindros de 16065 * 1024 = 16450560 bytes
Identificador de disco: 0x0004731c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
```

> **srs5694 said:**
> Also, how were you mounting the contents of that disk before you decided to convert it from FAT? How did you set the disk up in the first place? 
I bought a Samsung drive which came preformatted with FAT32.

---

### Post by leoh on 2010-03-12
For some reason now I can't access the filesystem in the disk.

> **coffeecat said:**
> In Gparted, go to Device > Create Partition Table. After you click on 'apply' for this you'll have a completely unallocated drive. Now create whatever partitions you want and see if this fixes the problem.

After clicking "apply", GParted closes with no error message or anything.
Why does GParted show a blank 298 GB drive? The rest of Ubuntu sees a 640 GB drive!

---

### Post by coffeecat on 2010-03-12
> **leoh said:**
> After clicking "apply", GParted closes with no error message or anything.

That sounds as if Gparted is crashing before it has created a new partition table. Which version of Ubuntu are you running? Are you running Gparted from a hard disk install? If so, try booting up from the Karmic live CD and see if Gparted in that works without crashing.

---

### Post by srs5694 on 2010-03-12
First, it sounds as if the disk came preformatted as a FAT "superfloppy." I can't be positive of that, though. If I'm right, then when you created the partition table, that corrupted the FAT filesystem on the disk, so it became inaccessible. Presumably this isn't a problem, since you said you were trying to replace it with something else anyway....

It does sound like a GParted bug is causing it to misreport the disk size. I notice this in your fdisk output:

```

Unidades = cilindros de 16065 * 1024 = 16450560 bytes

```

This looks to me as if the disk is reporting that it has 1024-byte sectors, whereas most disks has 512-byte sectors. (Note the equivalent line for /dev/sda, which uses a value of 512 instead of 1024 on the equivalent line.) If GParted has a bug that makes it assume 512-byte sectors, this would account for the misreported disk size. The partitions created by GParted might or might not be valid, given this bug. Therefore, I recommend using fdisk to create partition(s) on this disk. You'll need to use mkfs to create filesystem(s) on the partition(s) you create. Alternatively, you could try upgrading GParted, but I don't know if this bug is fixed in any particular version -- I don't even know that my supposition that it's a bug is correct! (It could instead be that fdisk is misreporting the sector size, but that would leave the misreport of the disk size by GParted a mystery. Occam's Razor therefore says that it's GParted with the bug.)

---

### Post by leoh on 2010-03-13
This is getting even stranger...

I am running Ubuntu 9.10 64 bits.
So I thought I could try with another computer. I went to another  Ubuntu (but 32 bits edition). Same story: shows as 298 GB and closes without any warning.

So... this is when this gets stranger: I downloaded the latest GParted stable version (0.5.2) on the original system... it doesn't even show the disk. However, it still appears on *lsusb* and *fdisk -l*.

Any ideas?

---

### Post by srs5694 on 2010-03-13
Did you read my previous reply? I'm pretty sure that your disk has 1024-byte sectors and that there's a bug in GParted (or more likely, libparted, upon which it relies) that's preventing it from working with such disks. In fact, I just tested with an old magneto-optical (MO) drive that uses 2048-byte sectors. I launched GParted from an xterm window, and it produced this output, then crashed:

```

# gparted /dev/sdd
======================
libparted : 1.9.0
======================
Device /dev/sdd has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

/usr/sbin/gparted: line 37: 31438 Segmentation fault      /usr/sbin/gpartedbin $*

```

The text-mode GNU Parted ("parted" command) didn't fare any better; it printed the same message about the sector size, then crashed when I tried a "print" command.

Please try launching GParted from a Terminal, Konsole, xterm, or similar text-mode shell window. If you see a message about support for your sector size being experimental, that's the problem. If so, just don't use GParted on this disk. Use fdisk instead; it works fine with such disks, in my (limited) experience.

---

### Post by leoh on 2010-03-14
Ok, I did that. I created a primary partition with fdisk.
Then I formatted the partition with mkfs. It appears as an ext3/ext4 partition (don't know which one it is, but I don't think I care).

However, I would like to rename the partition. I would like to change the disk (or partition) name to something more useful. Right now it shows as "640 GB filesystem" on the desktop, and it mounts on /media/92a10ed1-c74f-4aa3-a100-468765993a48.

Everywhere I read it says to rename it with gparted... which is not possible. What are the alternatives?

---

### Post by leoh on 2010-03-14
Nevermind, I solved it. Thank you guys!

---

