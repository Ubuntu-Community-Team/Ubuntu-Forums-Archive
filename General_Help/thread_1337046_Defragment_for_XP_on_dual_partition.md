---
title: "Defragment for XP on dual partition"
date: 2009-11-25
forum: General Help
---

### Post by kennethtb on 2009-11-25
Hi, firstly I know that to defrag Ubuntu is not necerserry - I have a dual partition system with Windows XP pro plus Ubuntu 9.10 - however when attempting to defrag Windows the  defrag facility shows a large part of disk C as being in need of defragging but upon running this facility it completes early with a message that it could not finish the job. I also tried with the Piriform Defraggler with this result ....
After defagging the Windows files it settles on local disk C: - File System NTFS - 1 file 16.4GB - 3 Total fragments - 71% in need of Fragmentation.  C:/ubuntu/disks/root.disk 
Finally the defrag process finishes (20 mins) but again (as with the Windows defrag facility) without completing ? but still showing a large portion of the disk as requiring urgent defragging. .. thoughts please

---

### Post by YosefKaro on 2009-11-25
Don't worry about that my friend.  I used to have Perfect Disk on Windows Vista and when a disk has a lot of defragging to be done, it cannot complete it all on one pass.  Sometimes, it requires many passes to be done to completely defrag.

-Yos

---

### Post by mixmaster on 2009-11-25
The windows defragger should not ever attempt to do anything with ubuntu partitions.  I'm not sure what c:/ubuntu/root.disk is - are you running WUBI or something like it?  I assume c: is your windows disk?

Note that some defrag operations cannot be carried out while the system is running windows.  Normally the debugger will offer to do an offline defrag which involves booting into some variant of dos and defragging the system disk from there.  If your defragger does not offer this option you are unlikely to be able to fully defrag c:.  Try PerfectDisk or O&O Debug (I think both have trial versions).

---

### Post by kennethtb on 2009-11-25
Hi thanks for your response - I have Ubuntu 9.10 installed with Windows XP Pro ( 50/50 partitions) and "yes" the windows defrag and the piriform defraggler are both attempting to defrag Ubuntu under drive C: and thats my question.  Also Ubuntu is listed in Windows XP .. control panel/add-remove which I thought was only forWindows?? .. if that means anything to anyone.

---

### Post by t0p on 2009-11-25
> **kennethtb said:**
> Hi thanks for your response - I have Ubuntu 9.10 installed with Windows XP Pro ( 50/50 partitions) and "yes" the windows defrag and the piriform defraggler are both attempting to defrag Ubuntu under drive C: and thats my question.  Also Ubuntu is listed in Windows XP .. control panel/add-remove which I thought was only forWindows?? .. if that means anything to anyone.

I think you must have done a **wubi** install of Ubuntu - that is, Ubuntu has been installed as an "application" in Windows rather than as a separate OS in its own partition.

I often see posts in these forums about odd problems in wubi installs that I have never heard of in a "proper" install.  Also I think wubi installs lack some properties of proper installs.

For that reason, I advise that a proper install of Ubuntu to its own partition is preferable if you plan to use Ubuntu at all seriously.

But I see that you said you *did* install Ubuntu to its own partition.  If you're sure that's the case... I don't know...

---

### Post by garvinrick4 on 2009-11-25
sdefrag c: /f in Windows does that not ask you to degrag on reboot when disc is not mounted.

Wubi install is in add and remove programs.

dual boot you have an  extended partition with linux and swap on two separate partitinos
inside of the extended partition. 

Kind of like sda/1 system and boot 
                 sda/2 ntfs
                 sda/3 extended partition
                 sda/4 linux
                 sda/5 swap
                 
Something near that sequence since XP does not have a D:drive which would have
sda/3. and move the rest up one.
 All the boots in sda/1      and grub 0/0 for sda/1    0/1 for sda/2    0/2 for sda/3  ect. ect. ect.

---

### Post by louieb on 2009-11-25
> **kennethtb said:**
>   Also Ubuntu is listed in Windows XP .. control panel/add-remove which I thought was only forWindows?? .. if that means anything to anyone.

It means you have WUBI (inside windows) install of Ubuntu. Confirmed by the file**   C:/ubuntu/disks/root.disk** - that is where Ubuntu is installed.  

[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide") 


BTW: [JkDefrag: A better windows defragmenter.]("http://kessels.com/JkDefrag/index.html")  works in XP - don't have Vista or Win 7 - so don't know.

---

### Post by t0p on 2009-11-25
To add to what I posted earlier: check out this passage from the [Wikipedia entry on wubi]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu_installer)"):

>  ubi adds an entry to the Windows boot menu which allows the user to run Linux. **Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk)**, as opposed to being installed within its own partition. This file is seen by Linux as a real hard disk

In particular, look at the bit I put in bold: that echoes what you said about c:\ubuntu\disks\root.disk.  I'd say you definitely have a wubi install.

I don't know anything about the need to defragment a wubi installed Ubuntu.

---

