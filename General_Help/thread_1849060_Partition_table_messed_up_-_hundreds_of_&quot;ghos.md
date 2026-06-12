---
title: "Partition table messed up - hundreds of &quot;ghost&quot; partitions"
date: 2011-09-23
forum: General Help
---

### Post by Quaxo76 on 2011-09-23
This all started with an attempt to restore a Windows partition. I don't know exactly where, but something went *very* wrong. Grub was obviously destroyed, and when I tried to recreate it, I couldn't. I'm now locked out of my system, and I can't do anything because the partition table of the hard disk is messed up... It had 10 or 11 partitions, but now it shows about 260. The first few seem "legitimate" but the following 250 are just many copies of two of the "legitimate" ones. (see my other post about GRUB for details...)
So, how can I try to recover my partitions? Is there a way to "recreate" the partition table? I tried downloading the GParted livecd, but it crashes with a Out of Memory kernel panic... maybe too many partitions?

Any ideas? I'm really at a loss... :(

Cristian

---

### Post by patryk77 on 2011-09-23
Try running testdisk from a live cd.

sudo apt-get install testdisk
sudo testdisk

Choose the analyse option.

---

### Post by YesWeCan on 2011-09-23
I think I can help fix this. What has gone wrong is the daisy-chaining of the extended partitions. It is as if one extended boot record is pointing back to an earlier one, thus creating a loop.

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9bca9bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    94928016    47462984+   7  HPFS/NTFS
/dev/sda2        94928024   129092767    17082372   83  Linux
/dev/sda3       129437694   976773119   423667713    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       190996848   194900579     1951866   82  Linux swap / Solaris
/dev/sda6       194900643   276816014    40957686   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7       276817920   308142079    15662080   83  Linux
/dev/sda8       308144128   369606655    30731264   83  Linux
/dev/sda9       369607518   459282284    44837383+  83  Linux
Partition 9 does not start on physical sector boundary.
/dev/sda10      459282348   542049164    41383408+  83  Linux
Partition 10 does not start on physical sector boundary.
[COLOR="DarkOrange"]/dev/sda11      369607518   459282284    44837383+  83  Linux
Partition 11 does not start on physical sector boundary.
/dev/sda12      459282348   542049164    41383408+  83  Linux
Partition 12 does not start on physical sector boundary.
/dev/sda13      369607518   459282284    44837383+  83  Linux
Partition 13 does not start on physical sector boundary.
/dev/sda14      459282348   542049164    41383408+  83  Linux[/COLOR]
```

Do you recall which partitions are supposed to be there. It appears that the sector addresses are obvious wrong starting at sda11. Did you have 10 partitions originally?

The method I would use is manual and tedious but will work. It is to look at each EBR in the chain until the one that is erroneous if found and then to fix it. Their locations are unknown but each one tells where the next one is.

To see the first EBR post the output of:
[COLOR="DarkSlateBlue"]sudo dd if=/dev/sda bs=512 count=1 skip=129437694 | hexdump -C[/COLOR]

---

### Post by srs5694 on 2011-09-23
I think that YesWeCan's diagnosis is correct. Editing the disk manually as he suggests can certainly effect a repair, but also as he says, it will be tedious (as well as prone to human error). You might want to try another couple of things first. I make no guarantees that either will work, but one of them might, and if so it will be an easier and safer fix than doing low-level disk editing directly:


[list]
[*]Try my [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. I've never tested it on a disk with your disk's problems, but it does include features that *might* make it reject all but the first instances of the duplicated partitions. OTOH, it might crash. If it reads the partitions and shows a reasonable partition list when you type "p" to view the partitions, or if it shows a list with all but one copy of each partition flagged as "omitted", it should be safe to write the partition table back out.
[*]Try typing "sudo sfdisk -d /dev/sda > parts.txt" and then examine the parts.txt file. I have no idea what sfdisk will do with the disk, but there's a slim chance that it will discard the duplicate partitions. Even if it doesn't, if it stops trying to read from the infinite loop at some point (as fdisk it), it will probably be easier to edit the parts.txt file to delete the duplicates and then write it back out with "sudo sfdisk -f /dev/sda < parts.txt" than to edit the disk on a low level with a hex editor or repeated uses of dd. If sfdisk keeps running for more than a second or two, though, you should interrupt it with a Ctrl+C keypress, since it's conceivable it'll try to fill the disk with an infinitely large parts.txt file!
[/list]


Note that both of these methods are likely to lose anything beyond /dev/sda10. There's significant space after that point on your original disk. The best way to recover those partitions is probably to use TestDisk, as patryk77 suggests. It's conceivable that TestDisk would do the job right when fed your currently-broken disk, but my inclination is to at least try to fix the current partition table before trying TestDisk on the disk.

---

### Post by patryk77 on 2011-09-24
> **srs5694 said:**
> [snip]...but my inclination is to at least try to fix the current partition table before trying TestDisk on the disk.

The reason I tend to suggest testdisk as the first option to fix partition tables is that if you run the Analyse mode, it generates the partition table for you without overwriting data before you accept the changes.

It never let me down or overwrote data, and IMO it's much safer than trying to fix anything manually (though I am not familiar with sfdisk).

Either way, I never had such a problem before, so I can't vouch that testdisk won't be confused either by whatever messed up the table in the first place.

---

### Post by Quaxo76 on 2011-09-24
Thank you all for your inputs. I'm going to try the "testdisk analyse" thing... I wanted to try that yesterday, but the gparted live I have downloaded doesn't boot. And with that system totally dead, it's not easy to go online and download things...
Anyway, I'll report as soon as I can try your suggestions!

Cristian

---

### Post by Quaxo76 on 2011-09-24
OK, I've tried testdisk. After selecting "analyse", it said:```
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

> 1 * HPFS - NTFS              0  32 33  5908 253 58   94925969                 
  2 P Linux                 5908 254  3  8035 166 35   34164744
  3 E extended              8057  31 37 60801  80 15  847335426
  5 L Linux Swap           11889   1  1 12131 254 63    3903732
    X extended             12132   0  1 17230 254 63   81915435
  6 L Linux                12132   1  1 17230 254 63   81915372
    X extended             17231   0  1 19180 244  8   31326065
  7 L Linux                17231  30 16 19180 244  8   31324160
    X extended             19181   0  1 23006 242 20   61463891
  8 L Linux                19181  21 41 23006 242 20   61462528
    X extended             23007   0  1 28588 254 63   89674830
  9 L Linux                23007   1  1 28588 254 63   89674767 [VirtualBoxVDI]
    X extended             28589   0  1 33740 254 63   82766880
    Next
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
>[Quick Search]  [ Backup ]
                            Try to locate partition
```

After starting "try to locate partitions" it quickly found these:
```


  HPFS - NTFS              0  32 33  5690  31 22   91409777
  Linux                 5908 254  3  8035 166 35   34164744
  Linux                 8057  31 39 11888 250 10   61558784
  Linux Swap           11889   1  1 12131 254 43    3903712
  Linux                12132   1  1 17230 254 59   81915368
  Linux                17231   1  1 19180 254 56   31326680 [VecchioRoot]
  Linux                19181   1  1 23006 254 60   61464624 [Home]
  Linux                23007   1  1 28588 254 56   89674760 [VirtualBoxVDI]
  Linux                28589   1  1 33740 254 62   82766816 [Musica]
  HPFS - NTFS          33740 254 63 62583 253 62  463362732
  Linux                33741   0  1 46621 254 62  206933264 [Appoggio]


```
Does that make sense? It's still searching, but I don't really remember having a second NTFS partition... I really think that shouldn't be there.
And I seem to recall there was another fairly large partition after the one named "appoggio", but maybe it still has to find it...
What do you think? I don't know how to read these results...

Cristian

---

### Post by YesWeCan on 2011-09-24
> **Quaxo76 said:**
> What do you think? I don't know how to read these results...
I think if this data is important to you then don't take chances with "no guarantees" short-cut advice; Why take the risk? I wouldn't.

---

### Post by srs5694 on 2011-09-24
One problem with TestDisk is that, because it uses CHS values where everybody else has abandoned them in favor of LBA values, it's hard to see how the filesystems it finds map onto existing or old partitions. There's a forumula on the [Wikipedia page for CHS](http://en.wikipedia.org/wiki/Cylinder-head-sector) to translate from CHS to LBA, so you can use that to see how the TestDisk results map onto those that your "fdisk -lu" output produced. If it's recovered all the correct partitions, and especially if it's also recovered anything that's been lost from beyond /dev/sda10, then having it finalize the changes makes sense. If TestDisk has *not* recovered some of your partitions (those shown by "fdisk -lu" or those that it's lost), you should be more cautious. You might want to save the start and end points for all the partitions (revealed by both "fdisk -lu" and TestDisk), use whatever method you like to create a legal partition table, and then patch up the rest with fdisk or sfdisk.

YesWeCan is certainly correct in suggesting that there are risks in such data recovery. This is true of *any* of the solutions suggested in this thread. At the very least, you should back up your current partition table with "sudo sfdisk -d /dev/sda > parts.txt" (assuming it completes its task and doesn't try to generate an infinite parts.txt file). In a pinch, the "fdisk -lu" data you've posted can be used to regenerate your partition table. Backing up your actual files is also worth doing, assuming Linux generates device nodes you can use to mount filesystems and do the backup. This obviously won't be possible for partitions beyond your /dev/sda10, though.

---

### Post by Quaxo76 on 2011-09-24
Testdisk finished the scan. The partition table it found does make sense somewhat, but sadly I can't be sure and remember exactly if everything is there. This is the output:

```
Disk /dev/sdb - 500 GB / 465 GiB - CHS 60802 255 63

The harddisk (500 GB / 465 GiB) seems too small! (< 514 GB / 479 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  HPFS - NTFS          33740 254 63 62583 253 62  463362732
```

It makes sense because I know I didn't have any NTFS partition, other than the primary one.
I have the outputs of fdisk -lu and of testdisk, now I'll make a backup of the partition table (and of the MBR) to be sure; then, maybe I'll try letting testdisk do its job... I don't think I have the skills needed to fix it by hand, or the free time to acquire them... :(

Thanks for now, I'll report when I have new info.

Cristian

---

### Post by YesWeCan on 2011-09-24
> **Quaxo76 said:**
> I don't think I have the skills needed to fix it by hand, or the free time to acquire them... :(
I am expert so you do not have to be. :-)
The process is:
[COLOR="DarkSlateBlue"]I tell you what command to run
You post the results
Repeat 10 times
Fixed.[/COLOR]

---

### Post by Quaxo76 on 2011-09-24
Heh... I like that plan... :) But about 40 minutes ago I sort of got excited about that testdisk output, and I allowed it to write the table... I still don't know if I should have done so or not. By the way, now the partitioning seems consistent. But the disc is still unbootable, because Grub was destroyed. At boot I get the GRUB2 shell (with the "grub>" prompt). Is there a quick way to reinstall it? My /boot folder is in /dev/sda2... And I confirmed that I can mount that partition and access the files in there. Once I can boot the system again, I can check if the other partitions are OK...

Cristian

---

### Post by YesWeCan on 2011-09-24
> **Quaxo76 said:**
> Heh... I like that plan... :) But about 40 minutes ago I sort of got excited about that testdisk output, and I allowed it to write the table... I still don't know if I should have done so or not.
Well I hope you got away with it but it is not the safest method.
> By the way, now the partitioning seems consistent. But the disc is still unbootable, because Grub was destroyed. At boot I get the GRUB2 shell (with the "grub>" prompt). Is there a quick way to reinstall it? My /boot folder is in /dev/sda2... And I confirmed that I can mount that partition and access the files in there. Once I can boot the system again, I can check if the other partitions are OK...

[edit] Follow this: [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)

Why not post
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]
so we can visually check the partition boundaries.

---

### Post by srs5694 on 2011-09-24
> **Quaxo76 said:**
> Heh... I like that plan... :) But about 40 minutes ago I sort of got excited about that testdisk output, and I allowed it to write the table... I still don't know if I should have done so or not. By the way, now the partitioning seems consistent. But the disc is still unbootable, because Grub was destroyed.

I recommend you boot using an emergency disk and run the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) This will create a file called RESULTS.txt with a wealth of partition and boot loader diagnostic information. Post that file here. With that information in hand, it should be possible to offer recovery advice.

---

### Post by Quaxo76 on 2011-09-25
@YesWeCan: I reinstalled GRUB using the command you gave me before the edit, and it worked - GRUB is there and seems to work.
The system still doesn't start though. During boot, I get the following messages:```
Problem mounting /VirtualBoxVDI
Press S to skip or M to mount manually
```
then I press M (because it's just a data partition) and I get ```
The disk drive for /home is not ready yet or not present.
Continue to wait; or press S to skip mounting or M for manual recovery
```
I pressed M again, thinking that it would boot anyway but with an empty home folder, but it gives errors about being unable to configure certain files and to create certain folders; and I end up with the Ubuntu background, the mouse pointer, and nothing else. 

I can run a terminal with Ctrl+alt+t, and I browsed the files, and I noticed that the mounts are all wrong... i.e. in the folder /XPlane, where it should mount the XPlane partition, it mounted the "Music" partition; and in the folder /Dati it mounted the root partition of an old system I keep around for emergencies.

Here is the output of fdisk -lu: ```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9bca9bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    91411824    45704888+   7  HPFS/NTFS
/dev/sda2        94928024   129092767    17082372   83  Linux
/dev/sda3       129437696   190996479    30779392   83  Linux
/dev/sda4       190996785   976784129   392893672+   f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       190996848   194900559     1951856   82  Linux swap / Solaris
/dev/sda6       194900643   276816010    40957684   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7       276816078   308142757    15663340   83  Linux
Partition 7 does not start on physical sector boundary.
/dev/sda8       308142828   369607451    30732312   83  Linux
Partition 8 does not start on physical sector boundary.
/dev/sda9       369607518   459282277    44837380   83  Linux
Partition 9 does not start on physical sector boundary.
/dev/sda10      459282348   542049163    41383408   83  Linux
Partition 10 does not start on physical sector boundary.
/dev/sda11      542049165   748982428   103466632   83  Linux
Partition 11 does not start on physical sector boundary.
/dev/sda12      947476480   976773119    14648320   83  Linux

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     7837695     3918832    b  W95 FAT32
```

When I try to mount the /home partition (sda8 ), I get an error saying "Stale NFS file handle".
When I try to mount sda7, I get this:```
mount: wrong fs type, bad option, bad superblock on /dev/sda7, missing codepage or helper program, or other error
```

Cristian

---

### Post by Quaxo76 on 2011-09-25
> **Quaxo76 said:**
> 

When I try to mount the /home partition (sda8 ), I get an error saying "Stale NFS file handle".


I should add that it is an ext3 partition, not a NFS. If I try to manually mount it as ext3, I get the same error that sda7 gives.

Cristian

---

### Post by Quaxo76 on 2011-09-25
I was able to "resurrect" an old "experimental" Linux partition (sda12). Now, that one boots. It seems that I can access most of the partitions except sda7 and sda8.
Of course, those are the ones where the most important data is.
And of course, I had a total backup on an external drive, but it was stolen from my office a few weeks ago, and of course I hadn't replaced it yet. :(

Cristian

---

### Post by YesWeCan on 2011-09-25
> **Quaxo76 said:**
> I was able to "resurrect" an old "experimental" Linux partition (sda12). Now, that one boots. It seems that I can access most of the partitions except sda7 and sda8.
Of course, those are the ones where the most important data is.
And of course, I had a total backup on an external drive, but it was stolen from my office a few weeks ago, and of course I hadn't replaced it yet. :(

Cristian
:-| I'll take a look at it this afternoon.

---

### Post by YesWeCan on 2011-09-25
```

**BEFORE**                                                                                
Device        Boot     Start                End        Sectors           GB          Blocks        Id        System                      gap from prev
/dev/sda1       *          2048         94928016        94925969        48.6        47462984+        7        HPFS/NTFS                          2047
/dev/sda2              94928024        129092767        34164744        17.5        17082372        83        Linux        ubuntu OS?               7
[COLOR="Blue"]/dev/sda3             129437694        976773119       847335426       433.8       423667713         5        Extended                         [/COLOR]344926
/dev/sda5             190996848        194900579         3903732         2           1951866        82        Linux        swap              61559153
/dev/sda6             194900643        276816014        81915372        41.9        40957686        83        Linux        ?                       63
/dev/sda7             276817920        308142079        31324160        16          15662080        83        Linux        [VecchioRoot]         1905
/dev/sda8             308144128        369606655        61462528        31.5        30731264        83        Linux        [Home]                2048
/dev/sda9             369607518        459282284        89674767        45.9        44837383+       83        Linux        [VirtualBoxVDI]        862
/dev/sda10            459282348        542049164        82766817        42.4        41383408+       83        Linux        [Musica]                63
[COLOR="DarkOrange"]/dev/sda11            369607518        459282284        89674767        45.9        44837383+       83        Linux                
/dev/sda12            459282348        542049164        82766817        42.4        41383408+       83        Linux                
/dev/sda13            369607518        459282284        89674767        45.9        44837383+       83        Linux                
/dev/sda14            459282348        542049164        82766817        42.4        41383408+       83        Linux        [/COLOR]        
                                                                                
**AFTER**                                                                                
Device        Boot     Start                End        Sectors           GB          Blocks        Id        System                      gap from prev
/dev/sda1       *          2048         [COLOR="Red"]91411824        91409777[/COLOR]        46.8        45704888+        7        HPFS/NTFS                          2047
/dev/sda2              94928024        129092767        34164744        17.5        17082372        83        Linux        ubuntu OS?         3516199
/dev/sda3             [COLOR="red"]129437696        190996479        61558784[/COLOR]        31.5        30779392        83        Linux        ?                   344928
[COLOR="blue"]/dev/sda4             190996785        976784129       785787345       402.3       392893672+        f        Extended                            [/COLOR]305
/dev/sda5             190996848        [COLOR="red"]194900559         3903712[/COLOR]         2           1951856        82        Linux        swap                    62
/dev/sda6             194900643        [COLOR="red"]276816010        81915368[/COLOR]        41.9        40957684        83        Linux        ?                       83
/dev/sda7             [COLOR="red"]**276816078**        308142757        31326680[/COLOR]        16          15663340        83        Linux        [VecchioRoot]           67
/dev/sda8             [COLOR="red"]**308142828**        369607451        61464624[/COLOR]        31.5        30732312        83        Linux        [Home]                  70
/dev/sda9             369607518        [COLOR="red"]459282277        89674760[/COLOR]        45.9        44837380        83        Linux        [VirtualBoxVDI]         66
/dev/sda10            459282348        [COLOR="red"]542049163        82766816[/COLOR]        42.4        41383408        83        Linux        [Musica]                70
[COLOR="DarkGreen"]/dev/sda11            542049165        748982428       206933264       105.9       103466632        83        Linux        [Appoggio]               1
/dev/sda12            947476480        976773119        29296640        15          14648320        83        Linux        ubuntu OS        198494051[/COLOR]

```

A lot has been changed. The notable exception is sda2 which I presume is your main Ubuntu OS. So the reason it is not booting is that it cannot mount /home and /VirualboxVDI. All other partitions have had their sizes changed. The NTFS has been shrunk a lot. sda3 has appeared out of nowhere and is the same size as sda8. A suspicious sign is that the starting sectors of sda7 & sda8 have changed and this may account for why they cannot be accessed.

First, some more info needed. Please mount sda2 and show the fstab contents
[COLOR="DarkSlateBlue"]sudo mount /dev/sda2 /mnt
cat /mnt/etc/fstab
sudo umount /mnt[/COLOR]

Then show the output of
[COLOR="DarkSlateBlue"]sudo blkid[/COLOR]

---

### Post by Quaxo76 on 2011-09-25
```
cristian@cristian-laptop:~$ sudo mount /dev/sda2 /mnt



cristian@cristian-laptop:~$ cat /mnt/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb2 during installation
UUID=67c95e1b-d39b-42af-972c-777ad1df53f1  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdb13 during installation
UUID=cdd507e5-77ce-4acf-8373-097a1bb74eee  /home        ext4  defaults             0  2  
# swap was on /dev/sdb5 during installation
UUID=cb5c309c-6a23-458e-bf41-229127bc260e  none         swap  sw                   0  0  
/dev/sda7                                  /VirtualBoxVDI  ext3  defaults             0  0 
/dev/sda12				/Dati	ext4	defaults	0	0
/dev/sda10				/XPlane	ext3	defaults	0	0
/dev/sda6				/Musica	ext3	defaults	0	0



cristian@cristian-laptop:~$ sudo umount /mnt



cristian@cristian-laptop:~$ sudo blkid

/dev/sda1: UUID="1BC30EAA31150B1E" TYPE="ntfs" 
/dev/sda2: UUID="67c95e1b-d39b-42af-972c-777ad1df53f1" TYPE="ext4" 
/dev/sda3: UUID="9d3d9054-1332-45af-b3d8-5fa4669f35f9" TYPE="ext4" 
/dev/sda5: UUID="cb5c309c-6a23-458e-bf41-229127bc260e" TYPE="swap" 
/dev/sda6: UUID="5f8a414f-37d8-4b4a-a3ac-186d3de737c1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="VecchioRoot" UUID="fdc98e9a-0d4d-41fe-bc2d-436e1a4fd9e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Home" UUID="ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba" TYPE="ext4" 
/dev/sda9: LABEL="VirtualBoxVDI" UUID="05e65efa-3dc8-4207-a5f8-3f6a79be5cb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Musica" UUID="ebe89e5f-2777-48ac-ab36-c3a8e8462153" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Appoggio" UUID="520e87f0-76c4-48ab-a2b3-9dd6594b7bc3" TYPE="ext4" 
/dev/sda12: UUID="729d163f-7515-428b-9eec-fe9ff65d7a61" TYPE="ext4" 

cristian@cristian-laptop:~$ 
```

I should add that (as I posted on another thread) when I try to access the disc with Gparted, it says "unallocated" - as if it was unpartitioned. Accessing it with Disk Utility does show the partitions.
I read somewhere that this can happen when there is an overlap, or when a partition exceeds the disk's boundaries.

Is it possible that all those start/end points were changed by testdisk because they weren't aligned with cylinder boundaries?

Cristian

---

### Post by Quaxo76 on 2011-09-25
The new sda3 that appeared from nowhere, and that has the same size as sda8, might be an old home partition. I usually keep two "root" partitions and two "home" partitions, of the same size, so that when I install a new Ubuntu, I can leave the old one alone, to "fall back" to if something goes wrong. Then at the next cycle, I wipe the oldest one and start again. So, sda3 might be legit.

Cristian

---

### Post by YesWeCan on 2011-09-25
> **Quaxo76 said:**
> ```
cristian@cristian-laptop:~$ sudo mount /dev/sda2 /mnt



cristian@cristian-laptop:~$ cat /mnt/etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb2 during installation
UUID=67c95e1b-d39b-42af-972c-777ad1df53f1  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdb13 during installation
UUID=[COLOR="Red"]cdd507e5-77ce-4acf-8373-097a1bb74eee[/COLOR]  /home        ext4  defaults             0  2  
# swap was on /dev/sdb5 during installation
UUID=cb5c309c-6a23-458e-bf41-229127bc260e  none         swap  sw                   0  0  
[COLOR="red"]/dev/sda7[/COLOR]                                  /VirtualBoxVDI  ext3  defaults             0  0 
[COLOR="red"]/dev/sda12[/COLOR]				/Dati	ext4	defaults	0	0
[COLOR="red"]/dev/sda10[/COLOR]				/XPlane	ext3	defaults	0	0
[COLOR="red"]/dev/sda6[/COLOR]				/Musica	ext3	defaults	0	0



cristian@cristian-laptop:~$ sudo umount /mnt



cristian@cristian-laptop:~$ sudo blkid

/dev/sda1: UUID="1BC30EAA31150B1E" TYPE="ntfs" 
/dev/sda2: UUID="67c95e1b-d39b-42af-972c-777ad1df53f1" TYPE="ext4" 
/dev/sda3: UUID="9d3d9054-1332-45af-b3d8-5fa4669f35f9" TYPE="ext4" 
/dev/sda5: UUID="cb5c309c-6a23-458e-bf41-229127bc260e" TYPE="swap" 
/dev/sda6: UUID="5f8a414f-37d8-4b4a-a3ac-186d3de737c1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="VecchioRoot" UUID="fdc98e9a-0d4d-41fe-bc2d-436e1a4fd9e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Home" UUID="ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba" TYPE="ext4" 
/dev/sda9: LABEL="VirtualBoxVDI" UUID="05e65efa-3dc8-4207-a5f8-3f6a79be5cb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Musica" UUID="ebe89e5f-2777-48ac-ab36-c3a8e8462153" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Appoggio" UUID="520e87f0-76c4-48ab-a2b3-9dd6594b7bc3" TYPE="ext4" 
/dev/sda12: UUID="729d163f-7515-428b-9eec-fe9ff65d7a61" TYPE="ext4" 

cristian@cristian-laptop:~$ 
```

I should add that (as I posted on another thread) when I try to access the disc with Gparted, it says "unallocated" - as if it was unpartitioned. Accessing it with Disk Utility does show the partitions.
I read somewhere that this can happen when there is an overlap, or when a partition exceeds the disk's boundaries.

Is it possible that all those start/end points were changed by testdisk because they weren't aligned with cylinder boundaries?

Cristian
The fact that GParted is showing "unallocated" is not good. Does it show a red circle with a ! that you can right click to see the information - what is it?

You'll need to edit fstab. The UUID for /home is no longer valid and should be replaced with the one from blkid. The /dev/sd7/12/10/6 entries should be replaced with UUID entries, again using the UUIDs from blkid.
[COLOR="DarkSlateBlue"]sudo mount /dev/sda2 /mnt
sudo gedit /mnt/etc/fstab
sudo umount /mnt[/COLOR]
Please post the new version for double-checking.

The thing I am concerned about is that you could not mount /home without that "Stale NFS file handle" error. I don't know what that means. If it were me, as a precaution, I'd back up sda7 & sda8 and then run a file system check before trying to boot the main Ubuntu. Have you got a spare drive?
file system check:
[COLOR="DarkSlateBlue"]sudo e2fsck /dev/sda8[/COLOR]

---

### Post by Quaxo76 on 2011-09-25
> **YesWeCan said:**
> The fact that GParted is showing "unallocated" is not good. Does it show a red circle with a ! that you can right click to see the information - what is it?

It's not a red circle, but a yellow triangle; anyway, it says "Warning: Can't have a partition outside the disk!"

Now I'll try fixing fstab as you said...

Cristian

---

### Post by Quaxo76 on 2011-09-25
This is the output of blkid:```
cristian@cristian-laptop:~$ blkid
/dev/sda1: UUID="1BC30EAA31150B1E" TYPE="ntfs" 
/dev/sda2: UUID="67c95e1b-d39b-42af-972c-777ad1df53f1" TYPE="ext4" 
/dev/sda3: UUID="9d3d9054-1332-45af-b3d8-5fa4669f35f9" TYPE="ext4" 
/dev/sda5: UUID="cb5c309c-6a23-458e-bf41-229127bc260e" TYPE="swap" 
/dev/sda6: UUID="5f8a414f-37d8-4b4a-a3ac-186d3de737c1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="VecchioRoot" UUID="fdc98e9a-0d4d-41fe-bc2d-436e1a4fd9e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Home" UUID="ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba" TYPE="ext4" 
/dev/sda9: LABEL="VirtualBoxVDI" UUID="05e65efa-3dc8-4207-a5f8-3f6a79be5cb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Musica" UUID="ebe89e5f-2777-48ac-ab36-c3a8e8462153" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Appoggio" UUID="520e87f0-76c4-48ab-a2b3-9dd6594b7bc3" TYPE="ext4" 
/dev/sda12: UUID="729d163f-7515-428b-9eec-fe9ff65d7a61" TYPE="ext4" 

```

And this is the fstab I edited:```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb2 during installation
UUID=67c95e1b-d39b-42af-972c-777ad1df53f1  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdb13 during installation
UUID=ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba  /home        ext4  defaults             0  2  
# swap was on /dev/sdb5 during installation
UUID=cb5c309c-6a23-458e-bf41-229127bc260e  none         swap  sw                   0  0  
UUID=05e65efa-3dc8-4207-a5f8-3f6a79be5cb9  /VirtualBoxVDI  ext3  defaults             0  0 
/dev/sda12				/Dati	ext4	defaults	0	0
UUID=5f8a414f-37d8-4b4a-a3ac-186d3de737c1	/XPlane	ext3	defaults	0	0
UUID=ebe89e5f-2777-48ac-ab36-c3a8e8462153      /Musica	ext3	defaults	0	0

```
As for the old /dev/sda12, called "Dati" in the old fstab, I don't know what to do, as I can't find it in blkid... I suppose it might be what now is sda7, but I seem to recall that it was quite larger than that...

Cristian

---

### Post by Quaxo76 on 2011-09-25
I was wondering, if tomorrow I buy a large external drive, and start backing up the data in known good partitions, and then delete those partitions, making the disk structure progressively emptier and simpler... would that help in recovering the lost ones?

Or even install a new system on the new disk, use the old one as external, and then proceed to move the data to the new disk? Would you say there are chances of saving the data that was in my /home and /Dati partitions?

Cristian

---

### Post by YesWeCan on 2011-09-25
Sorry, I have to rush out for an hour or two. Back later. :)

---

### Post by YesWeCan on 2011-09-25
> **Quaxo76 said:**
> It's not a red circle, but a yellow triangle; anyway, it says "Warning: Can't have a partition outside the disk!"
Yes, testdisk has cocked-up the extended partition end sector address. It is now 976784129 but the maximum is 976773167. The extended partition should finish at the last sector of sda12 which is 976773119.

To fix that you need to copy the partition table to a file and then edit the sda4 "size" value from 785787345 to **785776335**. Then write it back to the MBR.
[COLOR="DarkSlateBlue"]sudo sfdisk -d /dev/sda > pt.txt
sudo cp pt.txt ptbackup.txt
sudo gedit pt.txt[/color]
(and change the sda4 size entry)
[COLOR="DarkSlateBlue"]sudo sh -c "cat pt.txt | sfdisk /dev/sda"[/COLOR]
It is possible sfdisk will complain, post the error if so.
Once done GParted should show all the partitions.

---

### Post by YesWeCan on 2011-09-25
> **Quaxo76 said:**
> This is the output of blkid:```
cristian@cristian-laptop:~$ blkid
/dev/sda1: UUID="1BC30EAA31150B1E" TYPE="ntfs" 
/dev/sda2: UUID="67c95e1b-d39b-42af-972c-777ad1df53f1" TYPE="ext4" 
/dev/sda3: UUID="9d3d9054-1332-45af-b3d8-5fa4669f35f9" TYPE="ext4" 
/dev/sda5: UUID="cb5c309c-6a23-458e-bf41-229127bc260e" TYPE="swap" 
/dev/sda6: UUID="5f8a414f-37d8-4b4a-a3ac-186d3de737c1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="VecchioRoot" UUID="fdc98e9a-0d4d-41fe-bc2d-436e1a4fd9e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Home" UUID="ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba" TYPE="ext4" 
/dev/sda9: LABEL="VirtualBoxVDI" UUID="05e65efa-3dc8-4207-a5f8-3f6a79be5cb9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: LABEL="Musica" UUID="ebe89e5f-2777-48ac-ab36-c3a8e8462153" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Appoggio" UUID="520e87f0-76c4-48ab-a2b3-9dd6594b7bc3" TYPE="ext4" 
/dev/sda12: UUID="729d163f-7515-428b-9eec-fe9ff65d7a61" TYPE="ext4" 

```

And this is the fstab I edited:```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sdb2 during installation
UUID=67c95e1b-d39b-42af-972c-777ad1df53f1  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sdb13 during installation
UUID=ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba  /home        ext4  defaults             0  2  
# swap was on /dev/sdb5 during installation
UUID=cb5c309c-6a23-458e-bf41-229127bc260e  none         swap  sw                   0  0  
UUID=05e65efa-3dc8-4207-a5f8-3f6a79be5cb9  /VirtualBoxVDI  ext3  defaults             0  0 
/dev/sda12				/Dati	ext4	defaults	0	0
UUID=5f8a414f-37d8-4b4a-a3ac-186d3de737c1	/XPlane	ext3	defaults	0	0
UUID=ebe89e5f-2777-48ac-ab36-c3a8e8462153      /Musica	ext3	defaults	0	0

```
As for the old /dev/sda12, called "Dati" in the old fstab, I don't know what to do, as I can't find it in blkid... I suppose it might be what now is sda7, but I seem to recall that it was quite larger than that...

Cristian
Maybe best to comment it out for now: [COLOR="DarkSlateBlue"]#/dev/sda12[/COLOR]

---

### Post by YesWeCan on 2011-09-25
> **Quaxo76 said:**
> I was wondering, if tomorrow I buy a large external drive, and start backing up the data in known good partitions, and then delete those partitions, making the disk structure progressively emptier and simpler... would that help in recovering the lost ones?

Or even install a new system on the new disk, use the old one as external, and then proceed to move the data to the new disk? Would you say there are chances of saving the data that was in my /home and /Dati partitions?

Cristian
Removing existing partitions doesn't help. So I would be inclined to clone the whole thing to the new disk. Then one can experiment on the original knowing one can always restore the original state.

I don't know what testdisk can do. It concerns me that the start sectors of sda 7 & sda8 have changed because, to this this properly, the whole filesystem inside the partitions need to be moved too. When you do this with GParted, for example, it can take a very long time. I don't know whether the partitions were moved properly or just the start and end sectors were changed.

There are various ways to figure it out but I am feeling a little cautious at this stage about doing anything that might write to those partitions before they are backed up.

> When I try to mount sda7, I get this: mount: wrong fs type, bad option, bad superblock on /dev/sda7, missing codepage or helper program, or other error
This is a serious error. This could be caused by the start sector being wrong.

> When I try to mount the /home partition (sda8 ), I get an error saying "Stale NFS file handle".
This error normally concerns Network File System mounting of partitions. It could be a red herring. Were you using NFS mounting before this incident occurred?

---

### Post by srs5694 on 2011-09-25
First, I recommend doing a low-level backup before you do *anything* else:


[list=1]
[*]Get another hard disk that's at least as large as the one you've got now, plug it in, and boot to an emergency system
[*]Verify that your current disk is /dev/sda when you reboot and that the new disk is /dev/sdb. (You can use fdisk to check the partition tables to verify disks' identities.) If these values have changed, it's OK, but you must adjust your procedures appropriately.
[*]Type "sudo dd if=/dev/sda of=/dev/sdb". This will back up /dev/sda to /dev/sdb. Thus, it's *imperative* that you get the device filenames right, or you'll wipe out all your data! Take your hands off the keyboard and triple-check the values before you hit the Enter key! This command is likely to take hours to complete, since it copies everything on the hard disk (even empty space).
[/list]


With this low-level backup in place, you'll be protected against further damage.

Editing the partition table using sfdisk as YesWeCan suggests can work; however, /dev/sda3 isn't the only problem partition. /dev/sda7 and /dev/sda8 are messed up, too, so they need to be changed, as well. You can try making these changes all at once or one at a time. Personally, I think I'd try all at once, out of concern that attempts to mount and access the filesystems during intervening steps might end up damaging them while they're in an improper state. OTOH, doing them one at a time reduces the number of variables in any one change, which can minimize the risk of confusion.

In post #10, you said that you made a backup of the partition table. If you did this with "sfdisk -d", you should be able to combine its good entries with the current partition table's good entries to fix everything in one fell swoop. Specifically, the earlier backup should have correct entries for /dev/sda3, /dev/sda7, and /dev/sda8. A current "sfdisk -d" output will have correct entries for /dev/sda11 and /dev/sda12. Thus, you can start from the current partition table's backup file and replace its entries for /dev/sda3, /dev/sda7, and /dev/sda8 from the earlier one to create a 100% correct partition table file. You could then input this new file with "sfdisk -f /dev/sda < correct-parts.txt" (assuming you store the edited file as "correct-parts.txt").

---

### Post by YesWeCan on 2011-09-25
Stay focussed on my prescriptions for the moment or it will all go wrong.

It will be helpful to run a fs dump on sda7 and sda8. This reads the fs superblock and will reveal if it cannot be found because it is in the wrong place relative to the start sector:

[COLOR="DarkSlateBlue"]sudo dumpe2fs -h /dev/sda7

sudo dumpe2fs -h /dev/sda8[/COLOR]

If they are obviously broken then the next step is to change the start sectors of those partitions back to what they originally were. But again, I would be cautious and clone the drive before doing this. Unless you are in a really hurry.

---

### Post by Quaxo76 on 2011-09-25
Hehe, you all gave me a lot to read and do... but I'm leaving the office in 5 minutes, so I can't do it right now. I'll try your suggestions in a couple of hours hopefully, and then I'll report back.
And tomorrow I'll try to buy a new hd to make a clone, and to replace the stolen one in the future...

I don't know how to express my gratitude for the help you're giving me! :)

Cristian

---

### Post by srs5694 on 2011-09-25
> **YesWeCan said:**
> Stay focussed on my prescriptions for the moment or it will all go wrong.

I disagree. I believe my suggestion to combine the output of two sfdisk outputs (if the earlier ones exist) will be a quicker, easier, and safer approach than doing it piecemeal. Attempting to diagnose filesystems from partitions that have had their start points changed, as you're now suggesting, is almost certainly a wild goose chase.

---

### Post by Quaxo76 on 2011-09-25
Update... I have followed the advice from comment #27 (resizing extended partition sda4) and it appears to have worked - at least, GParted now sees the partitioning. Now, before doing more damage, I'll wait until tomorrow, when I can buy a new external drive, to clone this one.

> This error normally concerns Network File System mounting of partitions. It could be a red herring. Were you using NFS mounting before this incident occurred?
No, never used NFS. It was an ext3. And as I said above, trying to mount it as ext3 gives an error.

> In post #10, you said that you made a backup of the partition table. If you did this with "sfdisk -d", you should be able to combine its good entries with the current partition table's good entries to fix everything in one fell swoop What I have is what I posted in this post and my previous post (see [http://ubuntuforums.org/showthread.php?t=1848954](http://ubuntuforums.org/showthread.php?t=1848954) ). Unfortunately I don't have a backup from when it was working.

Cristian

---

### Post by Quaxo76 on 2011-09-25
To add to my previous message: it is true that I don't have a partition table from when everything was OK, but I do have the output of "fdisk -lu" from before the modifications made by testdisk. The output is quoted on message #3 of this thread.

Interesting thing: now that GParted sees the partitions, I noticed that it says that sda11 is about 40% full, which would make sense... but if I mount it, it gets mounted without errors, but it appears empty... ?!?

Cristian

---

### Post by srs5694 on 2011-09-25
> **Quaxo76 said:**
> Update... I have followed the advice from comment #27 (resizing extended  partition sda4) and it appears to have worked - at least, GParted now  sees the partitioning. Now, before doing more damage, I'll wait until  tomorrow, when I can buy a new external drive, to clone this one.

At least you've making progress! Cloning the disk at this point certainly makes sense.

> **Quaxo76 said:**
> To add to my previous message: it is true that I don't have a partition table from when everything was OK, but I do have the output of "fdisk -lu" from before the modifications made by testdisk. The output is quoted on message #3 of this thread.

It's possible to edit the file you get from "sfdisk -d" using that output, but you've got to do some math to convert the partitions' end points to size values. In your case, you've got, from fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda7       276817920   308142079    15662080   83  Linux
/dev/sda8       308144128   369606655    30731264   83  Linux

```

Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. Thus, you'd get sfdisk entries like this:

```
/dev/sda7 : start=276817920, size= 31324160, Id=83
/dev/sda8 : start=308144128, size= 61462528, Id=83

```

Please check my arithmetic on those values. I've checked twice, but checking again is in order.

Before you implement this change, though, was it possible to access those partitions before you used TestDisk? If so, those values are almost certainly correct and it should be safe to use them. If not, there's a possibility that they were incorrect before, that TestDisk has found the correct values, and that both partitions have filesystem damage. This seems very improbable to me, but I can't rule out the possibility entirely.

The dilemma is that correcting either problem is risky if you correct the *wrong* problem. If you make the changes using sfdisk, thus restoring the old partitions, and in fact the new partition locations determined by TestDisk are correct, then you'll write one sector into a location within the valid filesystem, which could be harmless or could damage the filesystem. This risk is fairly low because it's one sector and because the partition table *had been* set up this way, so chances are the same sector was already used in this way. Still, it's possible that you'll do significant damage to the filesystem.

OTOH, if you assume the new partition table is correct, you can use fsck or e2fsck to try to fix it, as in "sudo fsck /dev/sda7". The danger here is that fsck might become confused and write a whole bunch of data in inappropriate locations, thus making things much worse than they are now.

Perhaps YesWeCan's suggestion to use dumpe2fs is intended to gather information intended to help discriminate between these cases; but it's rather unlikely to discover such information if the partition's start point is incorrect. If you've got a backup, and given the likelihood that the original partition table was correct for these two partitions, you'll probably get a much quicker fix by re-writing the partition table, rebooting into an emergency disk that won't auto-mount the filesystems, and then attempt a read-only mount, as in:

```

sudo mount -o ro /dev/sda7 /mnt

```

If that works and you can access the filesystems, then you might unmount them and use fsck on them just to be sure they're clean.

If this fails, it might be necessary to restore the partitions to their current state, use dd to restore the first 1 MiB or so of /dev/sda7 and /dev/sda8, and try again in another way.

> Interesting thing: now that GParted sees the partitions, I noticed that it says that sda11 is about 40% full, which would make sense... but if I mount it, it gets mounted without errors, but it appears empty... ?!?

It could be that TestDisk has misdetected /dev/sda11, or it could be that it's suffered some damage. It's probably best to attempt a repair of it after you make a backup and deal with the earlier partitions.

If you're lucky, fsck may be able to repair the problems. If not, there are at least two alternatives:


[list]
[*]The type of dumpe2fs command that YesWeCan suggested for /dev/sda7 and /dev/sda8 might produce useful data. (It might do so here because there seems to be data that's properly aligned for some tools to detect, but that's not the case for /dev/sda7, and probably not for /dev/sda8.)
[*]You can try GParted's partition-recovery tool. You'd need to delete /dev/sda11 and then use Device -> Attempt Data Rescue in GParted. I've heard of cases in which it does a better job than TestDisk, so it might work even when TestDisk failed.
[/list]


None of these options is guaranteed to work.

---

### Post by Quaxo76 on 2011-09-26
OK, thanks, I'm going to buy the new disk now, then make the backup. It scares me that if the backup process takes hours, and a single mistake while trying to fix the backup forces me to re-do it from scratch... it's going to be a lengthy process! :)

As for the damaged partitions... GParted shows that sda8 has data, too - about 7GB, or about 25%.
sda11 shows 31% used.
The only one that is really unrecognized is sda7, which also has a red circle with a ! next to it. 

Cristian

---

### Post by YesWeCan on 2011-09-26
> **Quaxo76 said:**
> OK, thanks, I'm going to buy the new disk now, then make the backup. It scares me that if the backup process takes hours, and a single mistake while trying to fix the backup forces me to re-do it from scratch... it's going to be a lengthy process! :)

As for the damaged partitions... GParted shows that sda8 has data, too - about 7GB, or about 25%.
sda11 shows 31% used.
The only one that is really unrecognized is sda7, which also has a red circle with a ! next to it. 

Cristian
GParted working - good.

Please post [COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR] when you have the new drive connected up and I'll tell you the correct cloning instruction.

Please also post the dumpe2fs outputs.

Don't do anything else. :!:

> The only one that is really unrecognized is sda7, which also has a red circle with a ! next to it.
I think if you right-click the red circle it should give you information.

---

### Post by Quaxo76 on 2011-09-26
I'm back... The clone is done (I didn't wait for instructions because cloning is one thing I can do:) having done it several times in the past).

Output from fdisk -lu:```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9bca9bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    91411824    45704888+   7  HPFS/NTFS/exFAT
/dev/sda2        94928024   129092767    17082372   83  Linux
/dev/sda3       129437696   190996479    30779392   83  Linux
/dev/sda4       190996846   976773119   392888137    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       190996848   194900559     1951856   82  Linux swap / Solaris
/dev/sda6       194900643   276816010    40957684   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7       276816078   308142757    15663340   83  Linux
Partition 7 does not start on physical sector boundary.
/dev/sda8       308142828   369607451    30732312   83  Linux
Partition 8 does not start on physical sector boundary.
/dev/sda9       369607518   459282277    44837380   83  Linux
Partition 9 does not start on physical sector boundary.
/dev/sda10      459282348   542049163    41383408   83  Linux
Partition 10 does not start on physical sector boundary.
/dev/sda11      542049165   748982428   103466632   83  Linux
Partition 11 does not start on physical sector boundary.
/dev/sda12      947476480   976773119    14648320   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bca9bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    91411824    45704888+   7  HPFS/NTFS/exFAT
/dev/sdb2        94928024   129092767    17082372   83  Linux
/dev/sdb3       129437696   190996479    30779392   83  Linux
/dev/sdb4       190996846   976773119   392888137    f  W95 Ext'd (LBA)
/dev/sdb5       190996848   194900559     1951856   82  Linux swap / Solaris
/dev/sdb6       194900643   276816010    40957684   83  Linux
/dev/sdb7       276816078   308142757    15663340   83  Linux
/dev/sdb8       308142828   369607451    30732312   83  Linux
/dev/sdb9       369607518   459282277    44837380   83  Linux
/dev/sdb10      459282348   542049163    41383408   83  Linux
/dev/sdb11      542049165   748982428   103466632   83  Linux
/dev/sdb12      947476480   976773119    14648320   83  Linux

Disk /dev/sdc: 16.1 GB, 16053960192 bytes
16 heads, 32 sectors/track, 61240 cylinders, total 31355391 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31355390    15677679+   b  W95 FAT32
```

Other commands:

```
ubuntu@ubuntu:~$ sudo dumpe2fs -h /dev/sda7
dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   VecchioRoot
Last mounted on:          <not available>
Filesystem UUID:          fdc98e9a-0d4d-41fe-bc2d-436e1a4fd9e6
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              981120
Block count:              3915835
Reserved block count:     195791
Free blocks:              2353243
Free inodes:              752794
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      894
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8176
Inode blocks per group:   511
Filesystem created:       Sun Apr 26 20:51:08 2009
Last mount time:          Mon May  3 13:57:05 2010
Last write time:          Mon May  3 13:57:24 2010
Mount count:              2
Maximum mount count:      21
Last checked:             Sun May  2 20:04:02 2010
Check interval:           15552000 (6 months)
Next check after:         Fri Oct 29 20:04:02 2010
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      e89e7d46-c15f-4d47-81e6-8dcbf7a182b0
Journal backup:           inode blocks
Journal superblock magic number invalid!
```

and

```
ubuntu@ubuntu:~$ sudo dumpe2fs -h /dev/sda8
dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   Home
Last mounted on:          <not available>
Filesystem UUID:          ab9b0a2b-0c46-4f86-a5cb-448ec40a74ba
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         not clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1913840
Block count:              7683078
Reserved block count:     384152
Free blocks:              5795503
Free inodes:              1893293
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1022
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8144
Inode blocks per group:   509
Filesystem created:       Thu Oct 29 18:35:54 2009
Last mount time:          Mon Oct 11 18:10:11 2010
Last write time:          Sun Sep 25 09:45:06 2011
Mount count:              12
Maximum mount count:      20
Last checked:             Sat Oct  2 09:48:17 2010
Check interval:           15552000 (6 months)
Next check after:         Thu Mar 31 09:48:17 2011
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Default directory hash:   half_md4
Directory Hash Seed:      82b2aeac-97c9-4433-a790-1b19ec777ce6
Journal backup:           inode blocks

ubuntu@ubuntu:~$ 

```

And for sda11, which is very important too:

```
ubuntu@ubuntu:~$ sudo dumpe2fs -h /dev/sda11
dumpe2fs 1.41.14 (22-Dec-2010)
Filesystem volume name:   Appoggio
Last mounted on:          /Appoggio
Filesystem UUID:          520e87f0-76c4-48ab-a2b3-9dd6594b7bc3
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6471680
Block count:              25866658
Reserved block count:     1293332
Free blocks:              17872022
Free inodes:              6442273
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1017
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              1
Flex block group size:    16
Filesystem created:       Sat May 15 12:13:48 2010
Last mount time:          Sun Sep 25 21:51:36 2011
Last write time:          Sun Sep 25 21:52:54 2011
Mount count:              9
Maximum mount count:      22
Last checked:             Sat May 15 12:13:48 2010
Check interval:           15552000 (6 months)
Next check after:         Thu Nov 11 12:13:48 2010
Lifetime writes:          31 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      80fcc56d-6347-45a2-92a7-cbb5b4a03d69
Journal backup:           inode blocks
FS Error count:           68
First error time:         Sat Sep 24 20:57:48 2011
First error function:     htree_dirblock_to_tree
First error line #:       586
First error inode #:      2
First error block #:      9249
Last error time:          Sun Sep 25 21:52:48 2011
Last error function:      htree_dirblock_to_tree
Last error line #:        587
Last error inode #:       2
Last error block #:       9249
Journal features:         (none)
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00000346
Journal start:            0

ubuntu@ubuntu:~$ 

```

Whew... It took 5 hours to make the clone, I hope I don't have to do it many times! :)
By the way... the transfer (over USB) was 31MB/s, much faster than the 6-10 MB/s I get when transfering regular files... Is the OS overhead really that much during normal writes?!? :o

Cristian

---

### Post by YesWeCan on 2011-09-26
> **Quaxo76 said:**
> I'm back... The clone is done (I didn't wait for instructions because cloning is one thing I can do:) having done it several times in the past).
Good stuff. That's a long time - USB is slow. As you may know the cloned partitions will have identical UUIDs to the original so booting will malfunction if you try to boot one with the other still connected.

> Whew... It took 5 hours to make the clone, I hope I don't have to do it many times! :)
By the way... the transfer (over USB) was 31MB/s, much faster than the 6-10 MB/s I get when transfering regular files... Is the OS overhead really that much during normal writes?!? :o
Something is causing overheads - it will depend on file sizes and how fragmented they are on the source disk. dd is simpler as it just does a byte by byte copy and so there is no fs overhead.


So all partitions have valid superblocks. sda7 is missing a journal - was it ext3?

Try a fs check on each:
[COLOR="DarkSlateBlue"]sudo e2fsck -f /dev/sdaX
[/COLOR]
Don't let it make any changes at this stage, just see what it reports.

---

### Post by Quaxo76 on 2011-09-26
Probably stupid question: at this stage, is it better to work on the original or on the clone? I'd say either is ok, but I thought I'd ask first! :)

Cristian

---

### Post by YesWeCan on 2011-09-26
> **Quaxo76 said:**
> Probably stupid question: at this stage, is it better to work on the original or on the clone? I'd say either is ok, but I thought I'd ask first! :)

Cristian
No right answer. I suppose it may be better to fix the original so that you can then back it up to the new drive.

---

### Post by YesWeCan on 2011-09-26
I should probably have said to use [COLOR="DarkSlateBlue"]sudo e2fsck -[COLOR="Blue"]**n**[/COLOR]f /dev/sdaX[/COLOR] so as not to ask you whether to fix anything. You don't want to fix anything at this stage because it is still not certain that the superblock found is the correct one. 

If may be necessary to restore the original start addresses for sda7 & sda8. The superblocks start 1024 bytes or 2 sectors from the partition start. The contents at the original locations can be seen using:

[COLOR="DarkSlateBlue"]sudo dd if=/dev/sda bs=512 count=4 skip=276817920 | hexdump -C[/COLOR] (for sda7)

[COLOR="DarkSlateBlue"]sudo dd if=/dev/sda bs=512 count=4 skip=308144128 | hexdump -C[/COLOR] (for sda8 )

A ext superblock looks like this (starts at 400H):

```
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000400  10 07 07 00 00 18 1c 00  99 67 01 00 3c 17 1b 00  |.........g..<...|
00000410  05 07 07 00 00 00 00 00  02 00 00 00 02 00 00 00  |................|
00000420  00 80 00 00 00 80 00 00  90 1f 00 00 00 00 00 00  |................|
00000430  03 e3 80 4e 00 00 16 00  [COLOR="Blue"]**53 ef**[/COLOR] 01 00 01 00 00 00  |...N....S.......|
00000440  02 e3 80 4e 00 4e ed 00  00 00 00 00 01 00 00 00  |...N.N..........|
00000450  00 00 00 00 0b 00 00 00  00 01 00 00 3c 00 00 00  |............<...|
00000460  42 02 00 00 7b 00 00 00  c5 4c 4a 29 86 0c 47 d6  |B...{....LJ)..G.|
00000470  a3 46 07 66 80 dc 5d c8  74 65 73 74 00 00 00 00  |.F.f..].test....|
00000480  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000004c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 c1 01  |................|
000004d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000004e0  08 00 00 00 00 00 00 00  00 00 00 00 da f8 3a 4d  |..............:M|
000004f0  5b 59 41 0f bf 14 82 80  11 e8 6a 86 01 01 00 00  |[YA.......j.....|
00000500  00 00 00 00 00 00 00 00  02 e3 80 4e 0a f3 02 00  |...........N....|
00000510  04 00 00 00 00 00 00 00  00 00 00 00 ff 7f 00 00  |................|
00000520  00 80 08 00 ff 7f 00 00  01 00 00 00 ff ff 08 00  |................|
00000530  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000540  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 08  |................|
00000550  00 00 00 00 00 00 00 00  00 00 00 00 1c 00 1c 00  |................|
00000560  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000570  00 00 00 00 04 00 00 00  56 08 02 00 00 00 00 00  |........V.......|
00000580  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

```

---

### Post by Quaxo76 on 2011-09-26
The e2fsck command:
- For sda7, says ```
Superblock has an invalid journal (inode 8).
Clear? no
```
- For sda8 and sda11 gives a huge amount of text (123KB for sda8 and 1.2MB for sda11). Of course I can't quote it here, but I attached them to this post.

The hexdump: it sort of seems to make sense, the "53 ef" pair of bytes are there. Dumps attached as well.

Now the question I'm scared to ask: sda7 and sda8 have some important data (especially 8) but probably the most important is in sda11. Given that I don't have the original start sector (the output from the first fdisk -lu doesn't include a valid sda11), is there no way to find the correct start? Is there a "magic string of bytes" we could search for around the place where we expect it to be?

Cristian

---

### Post by YesWeCan on 2011-09-26
It looks safe to restore the start and end sectors now using the same method as you used for the extended partition:
sda7: start=276817920, size=31324160
sda8: start=308144128, size=61462528
Re-run the fs check afterwards.

Not sure about sda11. I think your idea of searching within a likely sector range will bear fruit. I need to sleep on it. :)

---

### Post by Quaxo76 on 2011-09-27
OK, I corrected the partition table (while I was at it, I also corrected sda1, which had been "shrunk" by testdisk for no appartent reason).
After reboot, sda7 and 8 (and 1) appear to mount fine, and I seem to find the data there. :D :D

Running fsck -f /dev/sda7 says the filesystem is clean:```
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda7: 218195/979200 files (2.8% non-contiguous), 1218872/3915520 blocks
```

while checking sda8 gives lots of errors. But I still seem to be able to access the files...

Now, should I backup the file somewhere or let fsck fix it?

And for sda11: I suppose it should start somewhere after the end of sda10. Is there a "hex disk editor" program that I can use to check the hex data on the disk, to look for the actual start of the partition?
Also: if I manage to find the partition start sector, how do I calculate the partition end? GParted seems to know the approximate size, should I use that data?

Thanks,
Cristian

---

### Post by YesWeCan on 2011-09-27
> **Quaxo76 said:**
> OK, I corrected the partition table (while I was at it, I also corrected sda1, which had been "shrunk" by testdisk for no appartent reason).
After reboot, sda7 and 8 (and 1) appear to mount fine, and I seem to find the data there. :D :D

while checking sda8 gives lots of errors. But I still seem to be able to access the files...

Now, should I backup the file somewhere or let fsck fix it?
Good. With sda8 I suppose it depends on the errors. I reckon you should have fsck fix it to avoid any file corruption. You can always start again using the backup if necessary.

> And for sda11: I suppose it should start somewhere after the end of sda10. Is there a "hex disk editor" program that I can use to check the hex data on the disk, to look for the actual start of the partition?
One approach would be to dd a large area into a text file and then search it for hex strings like the magic number. I'll suggest something in a moment.
> Also: if I manage to find the partition start sector, how do I calculate the partition end? GParted seems to know the approximate size, should I use that data?
It should be possible to get another estimate from the superblock too - it will state the fs size in blocks.
Back soon.

---

### Post by Quaxo76 on 2011-09-27
Status update:
We're starting to see the light! :)
To recap what I've done:
- For sda1, sda7, sda8 I restored the start sector and size using what was there before testisk messed it up;
- For sda11, I think I understood what happened. Testdisk had found (and restored) a partition called "Appoggio", which in Italian means something like "Temporary". It must have been an old partition, deleted long ago; looks like Testdisk thought it was something to rescue, but it was not. I used a disk editor (called iBored, very slow but it worked) and started to search after that sector, and indeed after a few sectors I found the start of another partition, called "Dati" - which makes sense because that's the name of the folder where I had it mounted.
So I set the start sector of sda11 to two sectors before where I found the two "magic bytes", and the end sector to a few sectors before the start of sda12.
Saved, rebooted and... looks like sda11 is back! :) :) It also tests clean with fsck. The end sector is probably off, but if it is, it's now bigger than the filesystem, and not smaller - as I made it as big as it could be. How can I use the superblock to find the right size?

Anyway... The files seem to be readable on all partitions - I didn't check them all of course, but at first sight they are. Can I try booting the old system to see if it boots?
I attached the output of fsck on /dev/sda8, and it's a really big output. Should I try copying the files somewhere, in case fsck breaks it? Or is it safe enough?

Anyway, lesson #1 learned: testdisk is dangerous and doesn't know what it does, and it breaks also perfectly good partitions. :(

Cristian

---

### Post by YesWeCan on 2011-09-27
The original end sector of sda10 is 542049164. Normally, there has to be a gap of at least 1 sector for the EBR so sda11 cannot start before 542049166. Testdisk made it start at 165.

First dump 165 and let's see if it is an EBR; if so it will give the start sector for sda11 relative to the original sector of the first EBR. The EBR sector will end with "55 aa".

[COLOR="DarkSlateBlue"]sudo dd if=/dev/sda bs=512 count=1 skip=542049165 | hexdump -C[/COLOR]

You can dump sectors and search for the "Appogio" sequence:
[COLOR="DarkSlateBlue"]sudo dd if=/dev/sda bs=512 count=10000 skip=542049165 | hexdump -C | grep -e "Appog"[/COLOR]

---

### Post by YesWeCan on 2011-09-27
I missed your post! Sounds like you are really getting the hang of this. :)
> **Quaxo76 said:**
> Status update:
We're starting to see the light! :)
To recap what I've done:
- For sda1, sda7, sda8 I restored the start sector and size using what was there before testisk messed it up;
- For sda11, I think I understood what happened. Testdisk had found (and restored) a partition called "Appoggio", which in Italian means something like "Temporary". It must have been an old partition, deleted long ago; looks like Testdisk thought it was something to rescue, but it was not. I used a disk editor (called iBored, very slow but it worked) and started to search after that sector, and indeed after a few sectors I found the start of another partition, called "Dati" - which makes sense because that's the name of the folder where I had it mounted.
So I set the start sector of sda11 to two sectors before where I found the two "magic bytes", and the end sector to a few sectors before the start of sda12.
Saved, rebooted and... looks like sda11 is back! :) :) It also tests clean with fsck. The end sector is probably off, but if it is, it's now bigger than the filesystem, and not smaller - as I made it as big as it could be. How can I use the superblock to find the right size?
If fsck -f is clean then don't touch it! :p

> Anyway... The files seem to be readable on all partitions - I didn't check them all of course, but at first sight they are. Can I try booting the old system to see if it boots?
I attached the output of fsck on /dev/sda8, and it's a really big output. Should I try copying the files somewhere, in case fsck breaks it? Or is it safe enough?
Wait while I look.

> Anyway, lesson #1 learned: testdisk is dangerous and doesn't know what it does, and it breaks also perfectly good partitions. :(
Lesson learned? This is why I recommended manually finding the EBRs and fixing them. ;)

---

### Post by YesWeCan on 2011-09-27
I am not knowledgeable enough to discern much from the fsck for sda8. Inode 7 is toast and there are free block count mismatches. Obviously, don't try to fix it while it is mounted.

You could make a new 40GB partition on the new drive and copy the contents of sda8 to it before you repair it.

[COLOR="DarkSlateBlue"]sudo rsync -vax /dev/sda8 /dev/sdbX[/COLOR]

I'd probably just repair it.

When all this is working well enough, for absolute certainty, I would suggest you boot a live CD/USB and reformat the new drive, then manually create partitions on it into which you can copy the contents of the old partitions. This way you end up with perfect file systems. Then adjust the UUIDs in fstab files and reinstall Grub. Then you can dd clone the new drive back to the 500GB one. This will take a lot of time and I don't know whether this is strictly necessary.

I recommend [COLOR="DarkSlateBlue"]rsync -ax --progress[/COLOR] for copying partition contents

---

### Post by Quaxo76 on 2011-09-27
> **YesWeCan said:**
> 
Lesson learned? This is why I recommended manually finding the EBRs and fixing them. ;)

I know... I was getting anxious and impatient and it looked like testdisk knew what it was doing, and its partition table seemed to make sense... Who knew it would change start and end point like that! :/

Cristian

---

### Post by YesWeCan on 2011-09-27
> **Quaxo76 said:**
> I know... I was getting anxious and impatient and it looked like testdisk knew what it was doing, and its partition table seemed to make sense... Who knew it would change start and end point like that! :/

Cristian
You weren't to know. You have to be very careful about using automated tools on critical data. And you have to carefully vet recommendations you receive to make sure the tools are proven to do the job properly. TestDisk is an experts tool and is not smart enough to know which partition remnants are the current ones. But what really worries me is that it created an illegal extended partition end sector! There is no excuse for that. So treat all tools with healthy cynicism - don't assume the people who wrote them were competent.

And do regular backups from now on :)
[edit] Oops, I forgot you were doing that before! Sorry. Ok, from now on do not let anyone steal your backup drive. :p

---

### Post by Quaxo76 on 2011-09-27
> **YesWeCan said:**
> Ok, from now on do not let anyone steal your backup drive. :p

Hehe... I was keeping it in my locker at work, because I thought that would be safer than carrying it around with me every day, with the risk of dropping or loosing it... Maybe I should keep *two* backups, one at home and one always with me! :)

Repartitioning the drive makes sense because even before having this problem, GParted always warned me that the partitions' boundaries were not aligned with cylinders, possibly ending in poor performance. Every attempt at re-aligning without totally repartitioning failed... (they had become misaligned when I cloned my old, smaller, HD into the 500GB one). But: does RSync preserve ownership, permissions, etc. on files? After moving the files from the old, rescued, partition to the newly created one, does it just work after reinstalling Grub?

Now, to go back to the start... This all started when I tried to revive an old Windows partition (I need to use Windows for a few days, to interface with a certain hardware). If I decide to just wipe sda1 (the old Windows) and reinstall a new WinXP onto it... it will of course destroy GRUB, but is it safe to do so and then reinstall Grub? Or will I find myself deep in trouble again?

Cristian

---

### Post by YesWeCan on 2011-09-27
> **Quaxo76 said:**
> Hehe... I was keeping it in my locker at work, because I thought that would be safer than carrying it around with me every day, with the risk of dropping or loosing it... Maybe I should keep *two* backups, one at home and one always with me! :)
I back mine up to a USB drive but I encrypted the whole drive in case I lose it: [http://www.emcken.dk/weblog/archives/164-encrypted-usb-drive-in-ubuntu.html](http://www.emcken.dk/weblog/archives/164-encrypted-usb-drive-in-ubuntu.html)
"The Cloud" sounds like a good alternative but you'd need fast internet connection and you'd probably have to pay for the capacity you need. I haven't used it and I don't know how secure it is...I would encrypt my files first.

> Repartitioning the drive makes sense because even before having this problem, GParted always warned me that the partitions' boundaries were not aligned with cylinders, possibly ending in poor performance. Every attempt at re-aligning without totally repartitioning failed... (they had become misaligned when I cloned my old, smaller, HD into the 500GB one).
Actually, cylinders do not exist any more as such. That is to say the boundaries are artificial now. An important thing is to align partition boundaries with physical  sectors rather than logical sectors if they are different. In the past, drives had both as 512 bytes but newer ones are now using bigger physical sectors, like 4096, to improve performance. The logical sectors are still 512 so the OS is happy. fdisk will tell you what your drive has.

> But: does RSync preserve ownership, permissions, etc. on files? After moving the files from the old, rescued, partition to the newly created one, does it just work after reinstalling Grub?
Yes rsync -a preserves everything and you can stop it mid-copy and then when you resume it, it carries on where it left off. Very useful tool.
After copying, the UUIDs of the new partitions will be different and this means the fstab(s) has to be adjusted and Grub has to be reinstalled.

> Now, to go back to the start... This all started when I tried to revive an old Windows partition (I need to use Windows for a few days, to interface with a certain hardware). If I decide to just wipe sda1 (the old Windows) and reinstall a new WinXP onto it... it will of course destroy GRUB, but is it safe to do so and then reinstall Grub? Or will I find myself deep in trouble again?
It should be ok to do that.
The other thing you could do is install Grub to another drive, like a USB stick, first. Then you could boot the USB to get to your OSs while leaving the standard MBR which XP will install in sda.

Remember, don't have the new drive connected when you boot because currently it has duplicate UUIDs and this may cause the wrong partitions to be mounted.

---

### Post by Quaxo76 on 2011-09-27
So... I backed up sda8 with dd, then ran fsck on it. And it reports clean now, and the files still seem accessible. I can't say for sure if *all* the files are there, but things are looking good. 
Then I fixed the old system's fstab (to reflect the recent changes) and tried booting it, as all the filesystems were reporting clean... And it works! I'm writing from my (revived) old partition now. Now I'll repartition the new drive and move the files there. I might use the new larger drive in the laptop and use the older as a backup...
I'm marking the thread as SOLVED now... and I want to thank again everyone who helped me fix my problem! I got my files back and learned a lot in the process.

> **YesWeCan said:**
> I back mine up to a USB drive but I encrypted the whole drive in case I lose it: [http://www.emcken.dk/weblog/archives/164-encrypted-usb-drive-in-ubuntu.html](http://www.emcken.dk/weblog/archives/164-encrypted-usb-drive-in-ubuntu.html)
"The Cloud" sounds like a good alternative but you'd need fast internet connection and you'd probably have to pay for the capacity you need.
Actually, I'm not overly concerned about security - I never store passwords or sensitive data on the data disks. It was mostly technical books that I had gathered in the years, or programs I had written, or other sorts of personal data. So, losing it is bad for me because I wouldn't have it anymore, not because anyone else would be interested in it... and btw I'm 99% sure that who stole my old hd just wiped it and resold it (it wasn't even FAT or NTFS, so it wouldn't show up in Windows, and I don't think the average thief knows about ext4!)

> An important thing is to align partition boundaries with physical  sectors rather than logical sectors if they are different. 
Yes, that's what it said, sorry, my mistake. The drive's physical sectors are 4KB while the logical sectors are 512bytes.


> 
The other thing you could do is install Grub to another drive, like a USB stick, first. Then you could boot the USB to get to your OSs while leaving the standard MBR which XP will install in sda.
I think I can also just backup and restore the MBR, right? If I prepare the partition for Windows first, with GParted, then do ```
dd if=/dev/sda of=/mbr.bin bs=446 count=1
```then install Win, then boot a livecd, mount root, and restore the mbr, then re-setup grub so it "sees" the new Windows... it should work, right?

Thanks again
Cristian

---

### Post by YesWeCan on 2011-09-27
> **Quaxo76 said:**
> I think I can also just backup and restore the MBR, right? If I prepare the partition for Windows first, with GParted, then do ```
dd if=/dev/sda of=/mbr.bin bs=446 count=1
```then install Win, then boot a livecd, mount root, and restore the mbr, then re-setup grub so it "sees" the new Windows... it should work, right?

Thanks again
Cristian
That should work. I normally advise people to do a live CD re-install to avoid the perils of a accident in the dd command.
[COLOR="DarkSlateBlue"]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
in your case.

Glad you sorted it out. :D

---

### Post by srs5694 on 2011-09-27
> **YesWeCan said:**
> But what really worries me is that it created an illegal extended partition end sector! There is no excuse for that.

This is a known problem with TestDisk. Some background (for Quaxo76; I expect you know this, YesWeCan): ~20 years ago, hard disks had a fixed number of cylinders, heads, and sectors, so disks' addressable space would be an exact multiple of a whole number of cylinders, heads, and sectors. Years ago, though, disk geometries became more complex, with a variable number of sectors per cylinder, so disks' firmware began producing CHS values that were convenient fictions. One consequence of this is that there were usually some "leftover" sectors after the last whole cylinder. Using CHS addressing, these were unusable, but using the newer LBA addressing, they're usable, and modern partitioning tools often *do* use them.

Based on tests I've performed, I suspect that TestDisk uses CHS addressing internally, and when it finds a filesystem that ends in this "leftover" area between the end of the last whole cylinder and the actual end of the disk, it creates an extended partition to hold the logical partition that's the size of a whole cylinder -- that is, too big for the disk. This is obviously a bug.

Fortunately, most OS kernels can handle such disks OK, and there's no risk of data loss in normal filesystem operations, since the logical partition that TestDisk creates is properly sized. Such a layout is technically illegal, though, and GParted tends to react to illegal disk layouts by displaying an empty partition table.

This problem can be corrected by using sfdisk to resize the extended partition, as YesWeCan directed you to do; or by using my [FixParts](http://www.rodsbooks.com/fixparts/) program, which rebuilds a fresh extended partition without using CHS values. In theory you could fix it with fdisk, but it would be tedious, since you'd need to re-create all your logical partitions. There are probably other non-Linux programs that can fix the problem, but I don't know what they are.

Of course, this is just a tiny part of the problem you encountered. I don't know what caused the infinite loop of EBR links that set off the whole thing. FWIW and IMO, the linked-list data structure of logical partitions is a weakness because such problems *can* occur with it. Most other partition table types, such as the Apple Partition Map (APM) or the GUID Partition Table (GPT), could not suffer from that specific problem, since they don't use linked-list data structures.

---

### Post by srs5694 on 2011-09-27
One other thing: In addition to regular data backups, keeping a backup of your partition table will enable easier recover if a problem like this recurs. The type of sfdisk output you've used to edit partition start and end points will do the trick:

```

sudo sfdisk -d /dev/sda > parts-sda.txt

```

If the partition table gets messed up, you can restore this to fix the problem. Be sure to keep your backup up to date, though; if you resize partitions with GParted, change partitions to install another OS, or whatever, restoring the old partition table will trash your changes!

---

