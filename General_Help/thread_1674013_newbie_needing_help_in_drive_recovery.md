---
title: "newbie needing help in drive recovery"
date: 2011-01-23
forum: General Help
---

### Post by attam on 2011-01-23
Yesterday, my windows partition (in a dual-boot with windows7/ubuntu) failed, and in trying to fix that partition, I managed to mess up both, including the MBR and what not :(
I have been desperately trying to recover them, and believe there's a good chance of doing that as I haven't yet written any data since the crash.
On running testdisk, I have the following info about them:
> [FONT=Courier New]
[FONT=Courier New]Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition            Start        End    Size in sectors
 1 P HPFS - NTFS              0  32 33   191  89 26    3072000 [TOSHIBA SYSTEM VOLUME]
 2 * HPFS - NTFS            191  89 27  5274 254 63   81668827 [S3A6747D002]
 3 P Linux                 5275   0  1 29494 254 59  389094296
 4 E extended LBA         29494 254 60 30401 254 63   14570959
 5 L HPFS - NTFS          29495   0  1 30400 254 54   14554881 [HDDRECOVERY][/FONT] [/FONT]
I am quite sure that the data I'm interested in recovering is in the partitions found on rows 2 and 3 (which correspond to my old windows drive c:, and my shared data drive, respectively).
currently, I am running off ubuntu that's living on my portable harddrive, and system>Disk Utility shows the internal (messed up) harddrive as one unpartitioned unknown mass of 250gb, with "bad sectors".

---

### Post by attam on 2011-01-23
update so far:
I used ddrescue to make an image of the disc and called it "sda_backup" with a corresponding logfile "logfile_sda". It took about 4 hrs for 250Gb.
I did it in 3 steps as described in the thread below:
> First you copy as much data as possible, without retrying or splitting sectors: 
[LIST]
[*]ddrescue --no-split /dev/hda1 imagefile logfile
[/LIST]
Now let it retry previous errors 3 times, using uncached reads: 

[LIST]
[*]ddrescue --direct --max-retries=3 /dev/hda1 imagefile logfile
[/LIST]
If that fails you can try again but retrimmed, so it tries to reread full sectors: 
ddrescue --direct --retrim --max-retries=3 /dev/hda1 imagefile logfileThen using mmls, I can read the contents of the image (see below):
> matta@matta-laptop:/media/New Volume$ mmls /media/New\ Volume/sda_backup -b
[FONT=Courier New]DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

     Slot    Start        End          Length       Size    Description[/FONT] [FONT=Courier New]
00:  Meta     0000000000   0000000000   0000000001   0512B   Primary Table (#0)
01:  -----   0000000000   0000002047   0000002048   0001M   Unallocated
02:  00:00   0000002048   0003074047   0003072000   0001G   NTFS (0x07)
03:  00:01   0003074048   0084742874   0081668827   0038G   NTFS (0x07)
04:  00:02   0084742875   0473837170   0389094296   0185G   Linux (0x83)
05:  Meta 0473837171   0488408129   0014570959   0006G   Win95 Extended (0x0F)
06:  Meta        0473837171   0473837171   0000000001   0512B   Extended Table (#1)
07:  -----   0473837171   0473837174   0000000004   0002K   Unallocated
08:  01:00   0473837175   0488392055   0014554881   0006G   NTFS (0x07)
09:  -----   0488392056   0488397167   0000005112   0002M   Unallocated[/FONT]
Now, I would like to be able to do something with that image, hopefully, get it readable so I can retrieve the data on my 185G Linux/ext3. I don't really care about the other partitions. Just the 185G one, which contains my documents, my family photos, and videos, etc.
I would appreciate anyone who can offer help...

---

