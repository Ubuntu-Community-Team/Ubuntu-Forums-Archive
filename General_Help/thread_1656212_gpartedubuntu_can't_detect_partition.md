---
title: "gparted/ubuntu can't detect partition"
date: 2010-12-30
forum: General Help
---

### Post by deadpool15 on 2010-12-30
hi, im running windows xp right now and im trying to isntall ubuntu. I ran boot the gparted cd up and it didnt detect my windows xp pro partition, it just said "unallocated space". I boot up the ubuntu cd and no partition was found either.

I think i might have done something wrong because I was running mint 9 and windows xp before. I decide to fresh install ubuntu and heres are the things i have done......

-recovery option - fixmbr then fixboot. 
-then in windows xp, disk management - delete all 3 mint 9 partitions (root,swap,home) leaving 80gb of unallocated space
-boot up gparted - no windows partition detected. 
-boot ubuntu same thing happen .

i tried this method I found in another thread


OK, then, it looks like you've got a new MBR with residual GPT data, which is confusing GParted. You'll have to wipe the GPT data. Here's how:

Boot your PartedMagic or System Rescue CD emergency disc.
For safety, back up your MBR by typing "dd if=/dev/sda of=sda-backup.mbr bs=512 count=1" and then copying the resulting file (sda-backup.mbr) to a USB flash drive, network share, or some other medium. Be sure to get the if= and of= parameters right, though!
Launch gdisk by typing "gdisk /dev/sda". When asked whether to use the MBR or GPT data, either will work.
Type "x" to enter the experts' menu. The command prompt should change.
Type "z" to "zap" (destroy) the GPT data. Tell it to proceed, but answer "N" to the question about blanking the MBR.

That's it. Windows should boot as it did before and you should now be able to continue your installation of Ubuntu; its installer should now see the same partitions as Windows.


but it still didnt work. any help?

---

### Post by coffeecat on 2010-12-30
> **deadpool15 said:**
> I ran boot the gparted cd up and it didnt detect my windows xp pro partition, it just said "unallocated space". I boot up the ubuntu cd and no partition was found either.

This usually means that there is something wrong with the partition table. Fortunately, this is usually fixable, but we need to do some investigation, particularly in view of the advanced partition table instructions you mention. They may or may not have been a good idea.

Boot up with an Ubuntu or Mint live CD - it doesn't matter which. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script. Post the RESULTS.txt file in code tags as described in that link. That will give us enough information to be able to see what might be wrong.

---

### Post by srs5694 on 2010-12-30
Please do as coffeecat suggests.

Also, a word of advice: ***never*** follow a procedure for a solution posted in another thread unless you're ***absolutely positive*** that the cause of your problem is the same as the cause of the problem described in the thread. Even if the symptoms seem similar, the causes of two problems may be very different, and what cures one problem could cause further damage for another one. In your case, you probably didn't do any further damage, but it's conceivable that you did, and in some configurations you would have. The procedure you followed (which I believe I posted) will overwrite data between the MBR and the first partition and at the very end of the disk. Some utilities, such as some boot loaders, store data in those locations, so overwriting the data in that way will just cause further problems.

I realize you've already done this, so any damage that's done is done. I'm posting mainly to head off future problems by somebody (you or somebody else who might read this) following a procedure they don't understand without first fully diagnosing their problem.

---

### Post by deadpool15 on 2010-12-30
thanks srs5694, i will always consider your advice. nonetheless, here's the code.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda4 starts at sector 148633443.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960    63,795,199    51,200,240   7 HPFS/NTFS
/dev/sda3          63,797,246   234,436,544   170,639,299   f W95 Ext d (LBA)
Empty Partition
/dev/sda4         148,633,443   234,436,544    85,803,102   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        8AFCF940FCF9275B                       ntfs                                     
/dev/sda2        F83007A830076D46                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        0428DED728DEC6B8                       ntfs       Documents                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/Documents         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  73 00 63 00 72 00 69 00  70 00 74 00 69 00 6f 00  |s.c.r.i.p.t.i.o.|
00000010  6e 00 5f 00 44 00 65 00  6c 00 65 00 74 00 69 00  |n._.D.e.l.e.t.i.|
00000020  6e 00 67 00 00 37 50 00  72 00 6f 00 70 00 65 00  |n.g..7P.r.o.p.e.|
00000030  72 00 74 00 79 00 44 00  65 00 73 00 63 00 72 00  |r.t.y.D.e.s.c.r.|
00000040  69 00 70 00 74 00 69 00  6f 00 6e 00 5f 00 44 00  |i.p.t.i.o.n._.D.|
00000050  65 00 6c 00 65 00 74 00  65 00 64 00 00 3b 50 00  |e.l.e.t.e.d..;P.|
00000060  72 00 6f 00 70 00 65 00  72 00 74 00 79 00 44 00  |r.o.p.e.r.t.y.D.|
00000070  65 00 73 00 63 00 72 00  69 00 70 00 74 00 69 00  |e.s.c.r.i.p.t.i.|
00000080  6f 00 6e 00 5f 00 49 00  6e 00 73 00 65 00 72 00  |o.n._.I.n.s.e.r.|
00000090  74 00 69 00 6e 00 67 00  00 39 50 00 72 00 6f 00  |t.i.n.g..9P.r.o.|
000000a0  70 00 65 00 72 00 74 00  79 00 44 00 65 00 73 00  |p.e.r.t.y.D.e.s.|
000000b0  63 00 72 00 69 00 70 00  74 00 69 00 6f 00 6e 00  |c.r.i.p.t.i.o.n.|
000000c0  5f 00 49 00 6e 00 73 00  65 00 72 00 74 00 65 00  |_.I.n.s.e.r.t.e.|
000000d0  64 00 00 39 50 00 72 00  6f 00 70 00 65 00 72 00  |d..9P.r.o.p.e.r.|
000000e0  74 00 79 00 44 00 65 00  73 00 63 00 72 00 69 00  |t.y.D.e.s.c.r.i.|
000000f0  70 00 74 00 69 00 6f 00  6e 00 5f 00 55 00 70 00  |p.t.i.o.n._.U.p.|
00000100  64 00 61 00 74 00 69 00  6e 00 67 00 00 37 50 00  |d.a.t.i.n.g..7P.|
00000110  72 00 6f 00 70 00 65 00  72 00 74 00 79 00 44 00  |r.o.p.e.r.t.y.D.|
00000120  65 00 73 00 63 00 72 00  69 00 70 00 74 00 69 00  |e.s.c.r.i.p.t.i.|
00000130  6f 00 6e 00 5f 00 55 00  70 00 64 00 61 00 74 00  |o.n._.U.p.d.a.t.|
00000140  65 00 64 00 00 57 45 00  6e 00 74 00 69 00 74 00  |e.d..WE.n.t.i.t.|
00000150  79 00 44 00 61 00 74 00  61 00 53 00 6f 00 75 00  |y.D.a.t.a.S.o.u.|
00000160  72 00 63 00 65 00 5f 00  43 00 6f 00 6d 00 6d 00  |r.c.e._.C.o.m.m.|
00000170  61 00 6e 00 64 00 54 00  65 00 78 00 74 00 4f 00  |a.n.d.T.e.x.t.O.|
00000180  72 00 45 00 6e 00 74 00  69 00 74 00 79 00 53 00  |r.E.n.t.i.t.y.S.|
00000190  65 00 74 00 4e 00 61 00  6d 00 65 00 00 67 45 00  |e.t.N.a.m.e..gE.|
000001a0  6e 00 74 00 69 00 74 00  79 00 44 00 61 00 74 00  |n.t.i.t.y.D.a.t.|
000001b0  61 00 53 00 6f 00 75 00  72 00 63 00 65 00 00 00  |a.S.o.u.r.c.e...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd 
```

---

### Post by coffeecat on 2010-12-31
I'm glad that srs5694 has joined the thread because his advice will be what you should follow. Let me make some observations and pose a question while we await his next post.

The reason that Gparted shows the drive as "unallocated" is that there is a problem in your partition table. It shows a primary partition - sda4 - within the space occupied by the extended partition sda3. This is an impossibility. A quick explanation in case you are unsure of the difference between the types of partitions. With a ms-dos/mbr type partition table you are limited to four primary partitions. To get around that limitation one (and one only) primary partition can be replaced by an extended partition. An extended partition is simply a specialised primary partition whose sole purpose is to "contain" a number of logical partitions. Primary partitions are numbered 1-4, logical partitions are numbered 5 upwards.

The next problem is trying to determine what sda4 is meant to be. sda1 is your Compaq diagnostics partition. sda2 is presumably your Windows C: partition - it contains the Windows boot files and has the boot flag set. sda4 is larger than sda2 but > According to the info in the boot sector, sda4 starts at sector 63.

Sector 63 being the start of sda1, your Compaq partition.

Question: can you boot into Windows? That is not clear from your first post. If so, what "drives" can you see in My Computer"?

The next step is probably to edit the partition table to deal with the sda3/4 contradiction, but exactly what you do may depend on your answers to the above.

---

### Post by srs5694 on 2010-12-31
Coffeecat's analysis looks correct to me. It seems to me that there are two ways to proceed:


[list]
[*]Delete /dev/sda3 (the extended partition). You'll probably have to create a new extended partition to install Ubuntu, but that's not a big deal. You can do this with fdisk; just launch it ("sudo fdisk /dev/sda"), select the "d" option, tell it to delete partition #3, and then type "w" to save your changes.
[*]Convert /dev/sda4 into a logical partition. This operation isn't directly supported by any standard partitioning tools I'm aware of, although it's possible with several, such as sfdisk and gdisk. To do it with sfdisk, you'd type "sudo sfdisk -d > parts.txt", edit parts.txt to change the number of /dev/sda4 to /dev/sda5, and then feed parts.txt back to sfdisk, as in "sudo sfdisk < parts.txt". Note that this procedure is from memory and I've not verified it, so I can't guarantee it'll work. Type "man sfdisk" and review any other documentation you can find before proceeding.
[/list]


Given that converting /dev/sda4 into a logical partition requires more knowledge and is a bit trickier, it's probably best to just delete /dev/sda3, unless you have a compelling reason to convert /dev/sda4.

Note also that there's a big pseudo-unallocated space between /dev/sda2 and /dev/sda4. Currently, /dev/sda3 starts at the beginning of this space, but there are no logical partitions in that space, hence my calling it "pseudo-unallocated" -- it's allocated to /dev/sda3, but /dev/sda3 isn't using it. Presumably you'll end up installing Linux in this space, but you might need or want to resize and/or move other partitions first, depending on your disk space needs. Post back with more details about what you want to do if you need advice on this matter.

---

### Post by deadpool15 on 2011-01-03
> **coffeecat said:**
> I'm glad that srs5694 has joined the thread because his advice will be what you should follow. Let me make some observations and pose a question while we await his next post.

The reason that Gparted shows the drive as "unallocated" is that there is a problem in your partition table. It shows a primary partition - sda4 - within the space occupied by the extended partition sda3. This is an impossibility. A quick explanation in case you are unsure of the difference between the types of partitions. With a ms-dos/mbr type partition table you are limited to four primary partitions. To get around that limitation one (and one only) primary partition can be replaced by an extended partition. An extended partition is simply a specialised primary partition whose sole purpose is to "contain" a number of logical partitions. Primary partitions are numbered 1-4, logical partitions are numbered 5 upwards.

The next problem is trying to determine what sda4 is meant to be. sda1 is your Compaq diagnostics partition. sda2 is presumably your Windows C: partition - it contains the Windows boot files and has the boot flag set. sda4 is larger than sda2 but 

Sector 63 being the start of sda1, your Compaq partition.

Question: can you boot into Windows? That is not clear from your first post. If so, what "drives" can you see in My Computer"?

The next step is probably to edit the partition table to deal with the sda3/4 contradiction, but exactly what you do may depend on your answers to the above.

Yes I can boot XP fine. here is an image i took from disk management from windows
[http://img812.imageshack.us/img812/5717/abcl.jpg](http://img812.imageshack.us/img812/5717/abcl.jpg)

from my understanding...

/dev/sd[COLOR=#FF0000]a[/COLOR][COLOR=#008000]1 [/COLOR]is partition [COLOR=#008000]1[/COLOR] of [COLOR=#FF0000]first hard disk[/COLOR], that corresponds to your windows 6G Compaq diagnostic partition
/dev/sda2 is partition 2 and corresponds to your window OS drive C: of 24G
/dev/sda3 is partition 3 and corresponds to your free space of 81G
/dev/sda4 is partition 4 and corresponds to your Documents, D: drive of 41G

base on srs5694 instruction, I should delete sd4 using fdisk, then save and rewrite tables. I just want to make sure i have the instruction correct before I do any changes.

---

### Post by coffeecat on 2011-01-03
> **deadpool15 said:**
> 
base on srs5694 instruction, I should delete sd4 using fdisk, then save and rewrite tables. I just want to make sure i have the instruction correct before I do any changes.

No. srs5694 suggested you could either delete sda[COLOR=Red]3[/COLOR] or convert sda4 into a logical partition, but that deleting sda3 was probably preferable.

I suggest you re-read my post about the difference between primary, extended and logical partitions, and also re-read srs5694's latest post. It's best that you understand as much as you can about partitions before you proceed. I'm afraid the information in the XP disk management utility is very oversimplified and could easily mislead. Although much harder to read, this part of your boot script output tells a more complete story:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,594,960    63,795,199    51,200,240   7 HPFS/NTFS
/dev/sda3          63,797,246   234,436,544   170,639,299   f W95 Ext d (LBA)
Empty Partition
/dev/sda4         148,633,443   234,436,544    85,803,102   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4
```If you look at the figures carefully, you'll see that sda4 appears to be inside sda3, which is impossible, and which is the source of your problem.

**EDIT**: to get the size of each partition from those figures, multiply the "size" figure (those are sectors) by 512 (the size of one sector) and then divide by 1,000,000,000 to get (base 10) GB. Windows is giving the sizes in GiB (base 2) which give lower figures, but it doesn't show the overlap between sda3 and sda4.

---

### Post by psusi on 2011-01-03
That screen shot shows that winders is retarded and does not recognize the extended partition in sda3 at all.  You want to delete it since it is broken.

---

### Post by deadpool15 on 2011-01-03
UPDATE: delete sda3 using fdisk just as srs5694 instructed and everything is running good now, im able to see my proper windows partition.

 SO MANY THANKS to srs5694, psusi, and coffeecat for helping fix this :grin::grin::grin::grin:=D>=D>=D>

---

