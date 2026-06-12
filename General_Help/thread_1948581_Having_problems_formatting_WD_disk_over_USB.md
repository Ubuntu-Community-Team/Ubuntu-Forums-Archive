---
title: "Having problems formatting WD disk over USB"
date: 2012-03-28
forum: General Help
---

### Post by tom17 on 2012-03-28
Hi,

I have been looking for info on my problem all morning but feel a bit stuck.

I just got a new WD20EARX (I understand this is the EARS just with SATA3) drive and a Thermaltake BlacX 5G USB3 dock for it. My intention is to use it on one of my Ubuntu machines but when I got home I plugged it into my Win7 laptop via USB3 to see what it was like and any attempt at formatting it just failed.

After this, I noticed the 'Advance Drive Format' stuff and learned that these drives are 4k physical sectors rather than 512b as before.

Plugged it all into my main PC (Asus P5B mobo, USB2.0 only, Ubuntu 10.04, yeah I know) and tried partitioning it & formatting it there and am still running into a wall with this thing.

Here is what I did:

Partitioning:
```
# parted /dev/sdf
GNU Parted 2.2
Using /dev/sdf
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s
(parted) p
Model: WDC WD20 EARX-00PASB0 (scsi)
Disk /dev/sdf: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  Type  File system  Flags

(parted) mkpart
Partition type?  primary/extended? primary
File system type?  [ext2]? ext4
Start? 2048
End? 3907029134
(parted) p
Model: WDC WD20 EARX-00PASB0 (scsi)
Disk /dev/sdf: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End          Size         File system  Name  Flags
 1      2048s  3907029134s  3907027087s  ext3

(parted) quit
Information: You may need to update /etc/fstab.

```
And formatting:
```
# mkfs.ext4 -T largefile4 /dev/sdf1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
476960 inodes, 488378385 blocks
24418919 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14905 block groups
32768 blocks per group, 32768 fragments per group
32 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000, 214990848

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: 
```

When I do the format, it hangs for like 40+ mins on the 'Writing superblocks' part.

The first time I did this, I was able to mount it, but as soon as I wrote to the FS, it remounted as readonly due to some errors.

I have repartitioned many times now, using gpt or mbr. I have set the first sector to 64, 2048 and others. I have formatted using ext4 & ext3. Every time I format I get the same delay on the last part.

Eventually I looked at the syslog while it was formatting to see what is going on and I repeatedly saw the following:

```
Mar 28 13:20:35 <hostname> kernel: [14393508.228609] sd 14:0:0:0: [sdf] Unhandled sense code
Mar 28 13:20:35 <hostname> kernel: [14393508.228613] sd 14:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 28 13:20:35 <hostname> kernel: [14393508.228617] sd 14:0:0:0: [sdf] Sense Key : Medium Error [current]
Mar 28 13:20:35 <hostname> kernel: [14393508.228622] sd 14:0:0:0: [sdf] Add. Sense: Peripheral device write fault
Mar 28 13:20:35 <hostname> kernel: [14393508.228626] sd 14:0:0:0: [sdf] CDB: Write(10): 2a 00 de c0 09 00 00 00 80 00
Mar 28 13:20:35 <hostname> kernel: [14393508.228636] end_request: I/O error, dev sdf, sector 3737127168
Mar 28 13:20:51 <hostname> kernel: [14393524.390590] sd 14:0:0:0: [sdf] Unhandled sense code
Mar 28 13:20:51 <hostname> kernel: [14393524.390594] sd 14:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 28 13:20:51 <hostname> kernel: [14393524.390598] sd 14:0:0:0: [sdf] Sense Key : Medium Error [current]
Mar 28 13:20:51 <hostname> kernel: [14393524.390603] sd 14:0:0:0: [sdf] Add. Sense: Peripheral device write fault
Mar 28 13:20:51 <hostname> kernel: [14393524.390607] sd 14:0:0:0: [sdf] CDB: Write(10): 2a 00 e8 00 09 80 00 00 80 00
Mar 28 13:20:51 <hostname> kernel: [14393524.390617] end_request: I/O error, dev sdf, sector 3892316544
Mar 28 13:20:51 <hostname> kernel: [14393524.390621] __ratelimit: 246 callbacks suppressed
Mar 28 13:20:51 <hostname> kernel: [14393524.390625] Buffer I/O error on device sdf1, logical block 3892314496
Mar 28 13:20:51 <hostname> kernel: [14393524.390627] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390631] Buffer I/O error on device sdf1, logical block 3892314497
Mar 28 13:20:51 <hostname> kernel: [14393524.390633] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390636] Buffer I/O error on device sdf1, logical block 3892314498
Mar 28 13:20:51 <hostname> kernel: [14393524.390639] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390642] Buffer I/O error on device sdf1, logical block 3892314499
Mar 28 13:20:51 <hostname> kernel: [14393524.390644] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390647] Buffer I/O error on device sdf1, logical block 3892314500
Mar 28 13:20:51 <hostname> kernel: [14393524.390649] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390652] Buffer I/O error on device sdf1, logical block 3892314501
Mar 28 13:20:51 <hostname> kernel: [14393524.390654] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390657] Buffer I/O error on device sdf1, logical block 3892314502
Mar 28 13:20:51 <hostname> kernel: [14393524.390659] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390662] Buffer I/O error on device sdf1, logical block 3892314503
Mar 28 13:20:51 <hostname> kernel: [14393524.390664] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390673] Buffer I/O error on device sdf1, logical block 3892314504
Mar 28 13:20:51 <hostname> kernel: [14393524.390675] lost page write due to I/O error on sdf1
Mar 28 13:20:51 <hostname> kernel: [14393524.390678] Buffer I/O error on device sdf1, logical block 3892314505
Mar 28 13:20:51 <hostname> kernel: [14393524.390680] lost page write due to I/O error on sdf1
```

Could this just be a faulty device or HD?

My next step is to try the HD internally, but that is a pain and the whole reason I got this dock for it.

My real questions here:
[LIST=1]
[*]Do AFD drives work in USB enclosures?
[*]Are AFD drives *formattable* in USB enclosures?
[*]Are there issues running a USB3 enclosure over USB2.0? (Although me having problems in Win7 too suggests not)
[*]Am I doing something wrong with regard to partitioning and formatting this AFD drive?
[*]Is my Ubuntu version too old for this stuff?
[*]Or is it more likely to just be a faulty drive or dock.
[/LIST]

Thanks,

Tom...

---

### Post by spcwingo on 2012-03-28
I've always had to "zero" disks that have been previously partitioned with gpt.  By "zero" I mean:

```
sudo dd if=/dev/zero of=/dev/sdf
```

After that just partition/format normally.

If that doesn't work, maybe it's a hardware problem.  I say that because of all of the I/O errors.

---

### Post by tom17 on 2012-03-28
Pretty sure this is HW now. Hope to god it's the Thermaltake dock. Don't feel like going through the RMA on a new drive. 

> # sudo dd if=/dev/zero of=/dev/sdf
dd: writing to `/dev/sdf': Input/output error

Syslog:
```
Mar 28 15:37:48 <hostname> kernel: [14401741.531319] sd 14:0:0:0: [sdf] Unhandled sense code
Mar 28 15:37:48 <hostname> kernel: [14401741.531323] sd 14:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 28 15:37:48 <hostname> kernel: [14401741.531328] sd 14:0:0:0: [sdf] Sense Key : Medium Error [current]
Mar 28 15:37:48 <hostname> kernel: [14401741.531332] sd 14:0:0:0: [sdf] Add. Sense: Unrecovered read error
Mar 28 15:37:48 <hostname> kernel: [14401741.531337] sd 14:0:0:0: [sdf] CDB: Read(10): 28 00 00 02 05 58 00 00 08 00
Mar 28 15:37:48 <hostname> kernel: [14401741.531346] end_request: I/O error, dev sdf, sector 132440
Mar 28 15:37:49 <hostname> kernel: [14401742.330727] sd 14:0:0:0: [sdf] Unhandled sense code
Mar 28 15:37:49 <hostname> kernel: [14401742.330731] sd 14:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 28 15:37:49 <hostname> kernel: [14401742.330735] sd 14:0:0:0: [sdf] Sense Key : Medium Error [current]
Mar 28 15:37:49 <hostname> kernel: [14401742.330740] sd 14:0:0:0: [sdf] Add. Sense: Peripheral device write fault
Mar 28 15:37:49 <hostname> kernel: [14401742.330744] sd 14:0:0:0: [sdf] CDB: Write(10): 2a 00 00 00 00 00 00 00 f0 00
Mar 28 15:37:49 <hostname> kernel: [14401742.330754] end_request: I/O error, dev sdf, sector 0
Mar 28 15:37:49 <hostname> kernel: [14401742.330758] __ratelimit: 50 callbacks suppressed
Mar 28 15:37:49 <hostname> kernel: [14401742.330761] Buffer I/O error on device sdf, logical block 0
Mar 28 15:37:49 <hostname> kernel: [14401742.330763] lost page write due to I/O error on sdf
Mar 28 15:37:49 <hostname> kernel: [14401742.330770] Buffer I/O error on device sdf, logical block 1
Mar 28 15:37:49 <hostname> kernel: [14401742.330772] lost page write due to I/O error on sdf
Mar 28 15:37:49 <hostname> kernel: [14401742.330775] Buffer I/O error on device sdf, logical block 2
Mar 28 15:37:49 <hostname> kernel: [14401742.330777] lost page write due to I/O error on sdf
Mar 28 15:37:49 <hostname> kernel: [14401742.330780] Buffer I/O error on device sdf, logical block 3
Mar 28 15:37:49 <hostname> kernel: [14401742.330782] lost page write due to I/O error on sdf

```

I guess I will need to plug the drive in directly tonight as a test...

Tom...

---

### Post by tom17 on 2012-03-29
Well it's starting to look like it's the Thermaltake BlacX dock that is the problem.

I have another WD2TB drive, I didn't realise yesterday, but it is the EARS version which also has AFD. I formatted this in 2010 without knowing about AFD and so it was partitioned incorrectly (Start sector of 63). This explains why I always found it a little slow - I always put this down to the USB interface of the enclosure it was in.

I tried the new drive in the old enclosure and it is working OK. I put the old drive in the new enclosure and you can read from it OK, but writes seem to fail with the same IO errors.

So it seems I can't write with this dock. It's either a compatibility problem between the dock and these EARS/EARX drives, compatibility problem between this USB3. dock running over USB2.0, or it's a faulty dock.

More tests to run on this. I guess this is more of a Thermaltake issue than an Ubuntu issue, so sorry I put it all here, I was desperate! lol

Tom...

---

