---
title: "ddrescue on a failing drive"
date: 2010-11-28
forum: General Help
---

### Post by endotherm on 2010-11-28
so I was asked to try to extract some data off a failing drive the other day. 
I plugged it in, but got no response in windows or linux (partition is ntfs), but it does appear in the bios and /dev (though the hdd hung most linux liveCDs except rescue remix 9.04).
I tried to analyze the drive, and found good smart data, so I figured there were just a few bad blocks in critical places. I ran spinrite against it in level 2 mode. the process crawled (40MB after 2 hours) and it updated the smart data to reflect many many reallocated sectors, putting the drive into a failing state as far as smart is concerned. 

so, now, in a last ditch effort I am turning to ddrescue to try to get an image of the drive. 
it's been running about 17 hours now, and has done several complete passes through "Splitting error areas".

here is my current output:
```

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dd6de08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS
root@ubuntu:~# sudo ddrescue -r 3 /dev/sdb /media/usb0/buimg1.iso /media/usb0/buimg1.log


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:    35233 kB,  errsize:    320 GB,  current rate:        0 B/s
   ipos:   130046 MB,   errors:       1,    average rate:      544 B/s
   opos:   130046 MB
Splitting error areas...

```so, should I give up? have I done all I can? can I in good conscious declare this a lost cause?

I do have an image from a prior run of ddrescue, with 826 MB of data. any idea if I can recover any of it? 

what'd ya think?

edit:
weird. I resumed the task from log, and now it is reporting the err size as 9223 PB. since the drive is a 320GB, I find that a bit odd.

---

### Post by endotherm on 2010-11-29
the silence in here is deafening. not a lot of hope then, eh?

---

