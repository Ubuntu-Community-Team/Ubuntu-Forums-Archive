---
title: "hard drive / partitioning troubles..."
date: 2009-11-30
forum: General Help
---

### Post by mdp189 on 2009-11-30
I dual boot windows XP (NTFS, on 40BG drive **/dev/sdb**) and ubuntu 8.10 (ReiserFS, on another 120GB hard drive **/dev/sda**).  There are also FAT32 partitions on both drives exclusively for data files.

I was repartitioning the second hard drive using *GParted *when something got screwed up... computer no longer booted (couldn't get to GRUB menu).

Specifically,

[LIST]
[*]I shrank the FAT32 partition **sda5** on the Ubuntu drive sda, no problem.
[*]Then I tried to create NTFS partition **sda8** in the empty space... got an error.
[*]Erased that partition again, tried to create reiserfs partition **sda8**... error.
[/LIST]
I have log files for those operations if it helps.  Suddenly, *GParted *no longer sees hard drives at all.  Upon reboot, blank screen/gibberish where GRUB menu loader used to be.

All data is now backed up (I used testdisk) on ipod or on my **sdb** (windows) drive.

I booted ubuntu 9 off a livecd... after going through *testdisk *and such for a day or two, I eventually was able to use *parted *to delete the **sda8** partition I had recently created and caused so much trouble.

After this, I could get the GRUB menu again, and boot into windows on **sdb **drive no problem. I can also boot into ubuntu on **sda**, I can mount and see all partitions fine, but it's unbearably slow and there are hundreds of errors in a pattern like the following in the system log:

> 
[  137.624825] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  137.624907] ata1.00: BMDMA stat 0x65
[  137.624976] ata1.00: cmd c8/00:08:35:01:20/00:00:00:00:00/e0 tag 0 dma 4096 in
[  137.624980]          res 51/40:08:35:01:20/00:00:00:00:00/e0 Emask 0x9 (media error)
[  137.625126] ata1.00: status: { DRDY ERR }
[  137.625187] ata1.00: error: { UNC }
[  137.665646] ata1.00: configured for UDMA/100
[  137.681200] ata1.01: configured for UDMA/100
[  137.681235] ata1: EH complete
and also some referring to specific sectors:

> 
[  147.817247] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  147.817258] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  147.817269] Descriptor sense data with sense descriptors (in hex):
[  147.817276]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  147.817298]         00 20 01 35 
[  147.817308] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  147.817321] end_request: I/O error, dev sda, sector 2097461
> 
[  667.933371] end_request: I/O error, dev sda, sector 4981485
[  683.789308] end_request: I/O error, dev sda, sector 16253317
[ 1298.525315] end_request: I/O error, dev sda, sector 16253448
[ 1549.289298] end_request: I/O error, dev sda, sector 17306381
During bootup in ubuntu it spends several minutes displaying these sorts of messages, and they continue to display in the virtual consoles (can't use those).   I don't see any errors like this in the system log files before saturday, the day I repartitioned.

I'm ok with just erasing the **sda **hard drive completely and reinstalling linux and putting the data back (I would use ntfs now, not fat32)... however, it seems like there are bad sectors? It seems strange this would start happening only after I repartition.

I got western digital's data lifeguard diagnostic utility... the hard drive SMART test says "Raw Read Error Rate" is at value 1 (the worst), where threshold is 51.  Everything else was ok with that test.  I ran longer tests and it quit right away saying "cable test failed, check the cables"?!  Well, I'll come back to this tomorrow.

I also still don't know why what I did (the simple repartitioning in *GParted*) caused such a mess.

---

### Post by dcstar on 2009-12-01
> **mdp189 said:**
> 
..........
I also still don't know why what I did (the simple repartitioning in *GParted*) caused such a mess.

Coincidence, hardware does fail.

---

