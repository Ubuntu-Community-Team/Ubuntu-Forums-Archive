---
title: "Ubuntu-XP Partitions and General Annoyance"
date: 2006-06-17
forum: General Help
---

### Post by Enders on 2006-06-17
**I know this is a long read, but please bare with me, I'm in some rather dire straights.**

Alright, I may have a major problem on my hands, and me being the linux noobie I am, need desperate help.

My computer consists of three physical drives, two being 18gb and another which is 80gb. The 80gb is partitioned so there is a 7gb(NTFS) and 66.85gb(NTFS). The 7gb holds my Windows OS. Another of the 17gb is partitioned into a 4gb(NTFS) and 13.99gb(FAT32). That leaves one last drive that I found to install Ubuntu on

I recently attemtped to install Ubuntu on one of of my physical drives. This drive was a 17.86gb(now ext3) drive that I formatted as NTFS called H: . I was quite positive that when I booted up Ubuntu Live and installed it to that drive. 

It went through the normal installtion, but upon restarting my computer, I met two errors.

On my main Ubuntu kernel selection in the GURB menu, I get this when I attempted to start it:
> Booting "ubuntu kernel name here..."
root (hd0,0)
File system type unknown, partion type 0x7
Kernel /boot/umlinuz-2.6.15-23-386
root=/dev/hda1 ro quiet splash

Error 17: Cannot Mount Selected Partition

Upon selecting my Microsoft Windows selection in the GURB menu, I got this:
> Booting...
root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
save default
make active
map (hd0(hd)
map(hd1)(hd0)
chainloader +1

Error 13: Invalid or unsupported executable format

I was sweating bullets. Did I accidentally format my C: drive upon installation?

I installed GParted to check things out. Everything seems to be fine. My 17gb ext3 and linux swap are on /dev/hda, my 80gb ntfs and what appears to be my C: drive, the 7.87gb ntfs are on /dev/hdb, and my other two drives are on /dev/hdc.

I was able to mount the /dev/hdc1, even though it's completely locked away from me because I don't have the right permission or something.

In the file browser, under Computer,  I can see my DVD drive and all my other drives, including the 17.8gb drive I supposdly installed Ubuntu on. Upon clicking on any of these, I get this:
> Unable to mount selected volume
error: device /dev/hdwhtevr is not removable

error: could not execute pmount

here is my fdisk -1
> fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


here is my nano /etc/fstab
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0
/dev/hdc1 /qdrive ntfs defaults 0 0






What I need to know from all this is:
-Is my C:/Windows drive screwed over.
-Is there a way to get all this back and having Ubuntu running smoothly WITHOUT having to reformat any of my normal drives besides the Ubuntu one

If anything else is required, please say so and I'll post it

---

### Post by hachaboob on 2006-06-17
Add the device to /etc/pmount.allow . This will bypass the is_removable check it seems.

---

### Post by Enders on 2006-06-17
[QUOTE=hachaboob]Add the device to /etc/pmount.allow . This will bypass the is_removable check it seems.[/QUOTE]
Explain further please, not quiet sure what you're getting at.

---

### Post by jstueve on 2006-06-17
post your fdisk -l (that is the lower-case L, phonetically ell)


for these: 
fdisk -l /dev/hda
fdisk -l /dev/hdb
fdisk -l /dev/hdc

(eh.. a 'dmesg | grep hd'  wouldn't hurt either)

---

### Post by KLineD on 2006-06-17
[QUOTE=Enders]Explain further please, not quiet sure what you're getting at.[/QUOTE]

Enders means that you should edit the file /etc/pmount.allow and add the devices there.

If you have access to a graphical environment:
```

sudo gedit /etc/pmount.allow

```

Or if you are stuck in console only:
```

sudo nano /etc/pmount.allow

```

---

### Post by Enders on 2006-06-17
I've recently restarted my computer in some hopes, so I no longer have any drives mounted. Just a heads up so you aren't put off balance by any differences

[QUOTE=jstueve]post your fdisk -l (that is the lower-case L, phonetically ell)


for these: 
fdisk -l /dev/hda
fdisk -l /dev/hdb
fdisk -l /dev/hdc

(eh.. a 'dmesg | grep hd'  wouldn't hurt either)[/QUOTE]
**fdisk -l /dev/hda**
```
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1307    10498446   83  Linux
/dev/hda2            2285        2434     1204875    5  Extended
/dev/hda3            1308        2284     7847752+  83  Linux
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris
/dev/hda6            2285        2330      369432   82  Linux swap / Solaris

Partition table entries are not in disk order
```

**fdisk -l /dev/hdb**
```
Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1028     8257378+   7  HPFS/NTFS
/dev/hdb2            1029        9729    69890782+   f  W95 Ext'd (LBA)
/dev/hdb5            1029        9729    69890751    7  HPFS/NTFS
```

**fdisk -l /dev/hdc**
```
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         608     4883728+   7  HPFS/NTFS
/dev/hdc2             609        2434    14666352    f  W95 Ext'd (LBA)
/dev/hdc5             609        2434    14666320+   b  W95 FAT3
```



[QUOTE=KLineD]Enders means that you should edit the file /etc/pmount.allow and add the devices there.

If you have access to a graphical environment:
```

sudo gedit /etc/pmount.allow

```

Or if you are stuck in console only:
```

sudo nano /etc/pmount.allow

```[/QUOTE]
I'll definatly try that, but I'd really like to worry less about mounting atm and more about getting into Windows/getting Ubuntu properly installed

EDIT:
I just recently attempted to install Ubuntu again, making a new 10gb partition of /dev/hda. 
Here's some shots from Gparted of my drives as they stand now

[[IMG]http://img222.imageshack.us/img222/7140/screenshot4cc.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshot4cc.png)
Spare drive with all Ubuntu stuff
[[IMG]http://img222.imageshack.us/img222/2025/screenshot24sx.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshot24sx.png)
80gb drive and smaller Windows drive
[[IMG]http://img90.imageshack.us/img90/4500/screenshot30ag.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshot30ag.png)
Two more drives, all stuff I'd rather not format.

---

### Post by Enders on 2006-06-17
[img]http://www.suxeh.net/images/bump.jpg[/img]

I really need to solve this. At the moment, my computer is completely useless aside from this Ubuntu Live CD which does nothing for me.

---

### Post by hachaboob on 2006-06-17
Show us your partitions and whether your harddrive(s) is SATA or PATA and your grub as it currently stands :KS

---

