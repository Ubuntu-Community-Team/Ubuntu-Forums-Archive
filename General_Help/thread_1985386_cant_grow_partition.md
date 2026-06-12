---
title: "cant grow partition"
date: 2012-05-23
forum: General Help
---

### Post by Kubischbuntu on 2012-05-23
Hi,

I am trying to grow a partition using the KDE Partition Editor and yes there is enough unallocated space behind that partition to grow into but it always comes back with an error I dont understand: 

 p, li { white-space: pre-wrap; }  Grow partition ‘/dev/sda2’ from 170.70 GiB to 320.17 GiB 
 Job: Check file system on partition ‘/dev/sda2’ 
 Command: ntfsresize -P -i -f -v /dev/sda2 
 ntfsresize v2011.4.12AR.4 (libntfs-3g) Device name        : /dev/sda2 NTFS volume version: 3.1 Cluster size       : 4096 bytes Current volume size: 183283913216 bytes (183284 MB) Current device size: 343783802880 bytes (343784 MB) Checking for bad sectors ... Checking filesystem consistency ... Accounting clusters ... Space in use       : 143299 MB (78.2%) Collecting resizing constraints ... Estimating smallest shrunken size supported ... File feature         Last used at      By inode $MFT               :        54 MB             0 Multi-Record       :    176095 MB         13280 $MFTMirr           :     91642 MB             1 Ordinary           :    183284 MB         30598 You might resize at 143298519040 bytes or 143299 MB (freeing 39985 MB). Please make a test run using both the -n and -s options before real resizing! 
Check file system on partition ‘/dev/sda2’: Success
Job: Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 671,452,740 
Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 671,452,740: Success

 Job: Resize file system on partition ‘/dev/sda2’ to 671,452,740 sectors 
 Resizing file system from 357,976,395 to 671,452,740 sectors. 
Resize file system on partition ‘/dev/sda2’ to 671,452,740 sectors: Error
Resize/move failed: Could not resize the file system on partition ‘/dev/sda2’ 
Job: Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 357,976,395 
 Could not set geometry for partition ‘/dev/sda2’ while trying to resize/move it. 
Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 357,976,395: Error
Could not restore old partition size for partition ‘/dev/sda2’. 
Resizing/moving partition ‘/dev/sda2’ failed. 
Grow partition ‘/dev/sda2’ from 170.70 GiB to 320.17 GiB: Error

Can anybody here enlighten me? 

Thanx

---

### Post by plucky on 2012-05-23
> Can anybody here enlighten me?


Can you post a screenshot of your Hard drive partitions?

---

### Post by muteXe on 2012-05-23
Silly question, but it's not mounted is it?

---

### Post by Kubischbuntu on 2012-05-23
I will post the screenshot when i get back home - and no it wasnt mounted - I un-mounted it first - that being said though I found it strange that after I tried to apply the change and got the error the partition appeared as mounted again.

---

### Post by wilee-nilee on 2012-05-23
> **Kubischbuntu said:**
> I will post the screenshot when i get back home - and no it wasnt mounted - I un-mounted it first - that being said though I found it strange that after I tried to apply the change and got the error the partition appeared as mounted again.

You have to use a live cd and have no partitions mounted, including the swap.

---

### Post by Kubischbuntu on 2012-05-23
> **wilee-nilee said:**
> You have to use a live cd and have no partitions mounted, including the swap.


Really?? I am fairly sure i have manipulated partitions on this machine before.

---

### Post by wilee-nilee on 2012-05-23
> **Kubischbuntu said:**
> Really?? I am fairly sure i have manipulated partitions on this machine before.

As long as it is not the one your running from it is okay, but unmount the swap. This unmounts the extended if around the whole thing and makes it safer as well in general.

Is is really hard to read your first post as well without some paragraphs at least for me anyway, so hard to tell what is really going on. ;)

---

### Post by Kubischbuntu on 2012-05-23
> **wilee-nilee said:**
> As long as it is not the one your running from it is okay, but unmount the swap. This unmounts the extended if around the whole thing and makes it safer as well in general.

Is is really hard to read your first post as well without some paragraphs at least for me anyway, so hard to tell what is really going on. ;)


Well OK I can add a bit more detail here. The partition i am trying to grow is a primary one. There is a heap of un-allocated space behind it (formerly occupied by another primary partition that has been deleted). It is this space I am trying to fill by growing sda2.  The OS and swap are in extended partitions - so quite separate.

Sorry for the formatting of the error log. It had paras when i copied it but lost them on pasting into here - will try again tonight.

---

### Post by wilee-nilee on 2012-05-23
> **Kubischbuntu said:**
> Well OK I can add a bit more detail here. The partition i am trying to grow is a primary one. There is a heap of un-allocated space behind it (formerly occupied by another primary partition that has been deleted). It is this space I am trying to fill by growing sda2.  The OS and swap are in extended partitions - so quite separate.

Sorry for the formatting of the error log. It had paras when i copied it but lost them on pasting into here - will try again tonight.

Just posting a screen shot of the partitioner, would be helpful for me.

---

### Post by Kubischbuntu on 2012-05-24
OK I have attached a snapshot of the partitioning - it is sda2 that I am trying to grow into the unallocated space behind it

---

### Post by wilee-nilee on 2012-05-24
The locks on each partition mean those partitions are mounted, look at my gparted, the sda3, sda6, and sd8 are mounted, the sda1 and sda2 are not.

---

### Post by Kubischbuntu on 2012-05-24
OK here is the full log file return for the operation including line breaks this time .... 

Turns out - there seems to be no way of pasting this in and retaining the formatting :mad: 

So I have attached it as a doc (I feel dirty now)

---

### Post by wilee-nilee on 2012-05-24
> **Kubischbuntu said:**
> OK here is the full log file return for the operation including line breaks this time:

                                        **Grow partition ‘/dev/sda2’ from 170.70 GiB to 305.39 GiB**  
  **Job: Check file system on partition ‘/dev/sda2’**  
  **Command: ntfsresize -P -i -f -v /dev/sda2**  
 [FONT=Courier New,courier]ntfsresize v2011.4.12AR.4 (libntfs-3g)[/FONT] [FONT=Courier New,courier]Device name        : /dev/sda2[/FONT] [FONT=Courier New,courier]NTFS volume version: 3.1[/FONT] [FONT=Courier New,courier]Cluster size       : 4096 bytes[/FONT] [FONT=Courier New,courier]Current volume size: 183283913216 bytes (183284 MB)[/FONT] [FONT=Courier New,courier]Current device size: 183283914240 bytes (183284 MB)[/FONT] [FONT=Courier New,courier]Checking for bad sectors ...[/FONT] [FONT=Courier New,courier]Checking filesystem consistency ...[/FONT] [FONT=Courier New,courier]Accounting clusters ...[/FONT] [FONT=Courier New,courier]Space in use       : 143397 MB (78.2%)[/FONT] [FONT=Courier New,courier]Collecting resizing constraints ...[/FONT] [FONT=Courier New,courier]Estimating smallest shrunken size supported ...[/FONT] [FONT=Courier New,courier]File feature         Last used at      By inode[/FONT] [FONT=Courier New,courier]$MFT               :        56 MB             0[/FONT] [FONT=Courier New,courier]Multi-Record       :    176095 MB         13280[/FONT] [FONT=Courier New,courier]$MFTMirr           :     91642 MB             1[/FONT] [FONT=Courier New,courier]Ordinary           :    183284 MB         30598[/FONT] [FONT=Courier New,courier]You might resize at 143396560896 bytes or 143397 MB (freeing 39887 MB).[/FONT] [FONT=Courier New,courier]Please make a test run using both the -n and -s options before real resizing![/FONT]  **Check file system on partition ‘/dev/sda2’: Success** **Job: Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 640,447,290** 
**Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 640,447,290: Success**
  **Job: Resize file system on partition ‘/dev/sda2’ to 640,447,290 sectors**  
 [FONT=Courier New,courier]Resizing file system from 357,976,395 to 640,447,290 sectors.[/FONT]  **Resize file system on partition ‘/dev/sda2’ to 640,447,290 sectors: Error** [FONT=Courier New,courier]Resize/move failed: Could not resize the file system on partition ‘/dev/sda2’[/FONT]  **Job: Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 357,976,395**  
 [FONT=Courier New,courier]Could not set geometry for partition ‘/dev/sda2’ while trying to resize/move it.[/FONT]  **Set geometry of partition ‘/dev/sda2’: Start sector: 208,845, length: 357,976,395: Error** [FONT=Courier New,courier]Could not restore old partition size for partition ‘/dev/sda2’.[/FONT]  [FONT=Courier New,courier]Resizing/moving partition ‘/dev/sda2’ failed.[/FONT]  **Grow partition ‘/dev/sda2’ from 170.70 GiB to 305.39 GiB: Error**

You need to have the sda2 unmounted that is all really if you want to make it bigger, no lock on that partition. Use a live cd if needed. If you have that partition in fstab as automounting you need to un-mount it.

You can't move or change a mounted linux ext partition period.

---

### Post by Kubischbuntu on 2012-05-24
> **wilee-nilee said:**
> You need to have the sda2 unmounted that is all really if you want to make it bigger, no lock on that partition. Use a live cd if needed. If you have that partition in fstab as automounting you need to un-mount it.

You can't move or change a mounted linux ext partition period.

I know that - the only reason it is mounted in the pic is that Firefox needs the partition when it is open - when I was trying to resize it - I closed everything that need the partition - then I first right clicked the partition - selected un-mount - the lock disappeared - then I did the re-sizing and clicked apply

---

### Post by wilee-nilee on 2012-05-24
> **Kubischbuntu said:**
> I know that - the only reason it is mounted in the pic is that Firefox needs the partition when it is open - when I was trying to resize it - I closed everything that need the partition - then I first right clicked the partition - selected un-mount - the lock disappeared - then I did the re-sizing and clicked apply

Not sure then, always has worked for me probably at least 500 times.

Use a live disc and see what happens.

---

### Post by Kubischbuntu on 2012-05-24
Never mind - managed to to it now. I booted into an older version of Kubuntu and it worked there straight off the bat. That is why I have several versions of Kubuntu on this machine - there are always some things that work on one version and not on others :rolleyes:

---

