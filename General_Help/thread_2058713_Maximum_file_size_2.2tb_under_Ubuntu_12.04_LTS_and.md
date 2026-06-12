---
title: "Maximum file size 2.2tb under Ubuntu 12.04 LTS and XFS?"
date: 2012-09-16
forum: General Help
---

### Post by scotjam1981 on 2012-09-16
I'm running Ubuntu Desktop 12.04 LTS 64 bit. I have attached a Highpoint Rocketraid 2680 with 8x1TB  drives attached with RAID 5 (resulting in a 7TB volume). 

I have successfully installed the drivers and formatted the disk (I first tried EXT3, but then EXT4 and now XFS format). 

However, I cannot create a file on the disk of greater than 2.2TB - once a file reaches that size, further writing fails. For example if I run the command:
```
dd if=/dev/zero of=/media/[mountpoint-of-raid-array]/big.tmp count=3500000 bs=1M
```
... it fails once big.tmp is 2.2TB

[http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html) has some useful pointers as to what the maximum file system sizes and file sizes are for each format, but XFS should easily cover my requirements given that it supports file sizes and file system sizes of up to 8 EiB.  

Any thoughts as to what the problem might be?

---

### Post by scotjam1981 on 2012-09-16
Ok, it looks like all I had to do was change the partition table to GPT using gdisk (using the "n" "v" and "w" commands), and using the default settings for the "n" command(including 8300 hex code) when prompted.

More detail here: [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

I'm not sure why this worked - I thought that it must already be a GPT partition table volume if it was recognized as a volume that was larger than 2.2TB (and Ubuntu could see a 6.3TB volume), but apparently GPT did the trick...

Incidently, for anyone wondering if the lack of a GPT partition table is their issue as well, you can see whether your volume uses GPT or not by running gparted and choosing View -> Device information. The output on my box(emphasis mine) is:
Device Information
Model: HPT DISK_6_0
Size: 6.37 TiB
Path: /dev/sdb

[B][I]Partition table: gpt
[/I][/B]Heads: 255
Sectors/track: 63
Cylinders: 851xxx
Total sectors: 13673xxxxxx
Sector size: 512

I hope that's helpful to anyone else facing the same problem

---

### Post by oldfred on 2012-09-16
If you use dd it does a low level copy and wipes out some of the internal gpt data. You should not use dd on gpt partitioned drives. 
It may work if copying the entire drive, but I would still not trust dd with any drive partitioning change.

---

### Post by scotjam1981 on 2012-09-16
oldfred - thank you for the reply - I just picked up the dd method for checking how much can be written from another forum post. Would there be an alternative to dd that could easily be used to test maximum file size on gpt?

EDIT - just to be 100% clear, I was not using DD to actually copy anything meaningful, just to create a big file (of zeros) on the drive, but I presume from your answer that that would still be unsafe?

---

### Post by oldfred on 2012-09-16
Are you just looking for the maximum that is supported?

[http://www.ibm.com/developerworks/linux/library/l-gpt/index.html](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html)

---

### Post by scotjam1981 on 2012-09-17
Thanks for your reply and for the gpt link. It's bizarre that dd seemed to work for me to create files larger than 2.2tb only once I had set my disk as gpt. Luck of the draw I guess.


In answer to your question, I'm looking for a way to practically test the maximum file size supported, by creating an expanding file full of dummy data (testing to failure). Because there are several potential sources of limitation (file system, OS, BIOS, etc) it is very difficult to determine actual maximum file size on a system without testing it. Is there an alternative to dd that could be used for that purpose? 

Many thanks for your help

---

### Post by oldfred on 2012-09-17
I am sorry, I just saw you using dd with gpt. You were actually copying to a file which should then be ok. It is trying to copy a partition that will corrupt the partition.

from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

---

### Post by scotjam1981 on 2012-09-17
oldfred, many thanks for clarifying. 

So to summarize, for anyone else reading this, the command: 
```
dd if=/dev/zero of=/media/[mountpoint-of-raid-array]/big.tmp count=3500000 bs=1M
```
should work to try to create a large file (3.5TB in this case) called big.tmp wherever you tell it your raid array is, thereby confirming whether you OS, BIOS, filesystem etc can support such large files. Having said that, it sounds like "dcfldd", which is basically dd with more features (including showing the copying progress - see [http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)) would be a more helpful choice than dd.

The solution to my issue (couldn't create files larger than 2.2TB on my raid array) was to change the partition table to GPT using gdisk (using the "n" "v" and "w" commands), and using the default settings for the "n" command (including 8300 hex code) when prompted (more detail on gdisk here: [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html))

I hope that helps someone!

---

