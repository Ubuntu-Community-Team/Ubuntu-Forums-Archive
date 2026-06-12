---
title: "Computer won't boot"
date: 2012-04-10
forum: General Help
---

### Post by Messyhair42 on 2012-04-10
Today I noticed noises from my computer fans so I blew out the dust with canned air like I always do, when I had everything reconnected my BIOS sequence was taking a long time and my GRUB screen never came up. after multiple restarts trying multiple BIOS sequences and OS's I was able to boot to my backup on a thumb drive. When I try to boot to my normal installation I simply get "READ ERROR." I took the cover off again and checked my cable connections. in every case my BIOS screen takes a long time and I can't boot to my other HD OS's either (W7 and Fedora 11). I also get a "click" from the hardware in sequence (one click several seconds apart, in groups with an indefinite gap between groups) (headstrike?)

from my backup I can see my partitions except the ones on the drive that contains both Fedora and Windows. On the drive with my main installation of Ubuntu 10.04 I can access some files (my entire pictures folder, but not my videos)

I'm asking for help because I haven't had anything like this happen before; I'm not convinced it's a big problem because I have had a lot of boot problems that seem to fix themselves that only require time, and then everything is back to normal. In any case I've described the sequence of events that led to this is as best detail I can in hopes there might be a quick and effective solution.

---

### Post by dcstar on 2012-04-11
> **Messyhair42 said:**
> 
........
In any case I've described the sequence of events that led to this is as best detail I can in hopes **there might be a quick and effective solution**.

Replace the dying hard drive.

---

### Post by Messyhair42 on 2012-04-11
> **dcstar said:**
> Replace the dying hard drive.

I think that's what I'll have to do. I've been able to get some of the data off the drive, I have most of it backed up but some isn't. It's still functioning but access to the drive is spotty. I would like to get my most recent bookmarks.html file since my backup is a week old. Any suggestions on getting some of the data off the drive?

---

### Post by IWantFroyo on 2012-04-11
If you have a /home partition, you should be able to access it from a live CD.
 
[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

---

### Post by Messyhair42 on 2012-04-15
My focus is now on recovering as much data as I can. Folders within /home have been slowly disappearing from my view in nautilus and now my USB installation won't let me mount /home (I can still mount other partitions on the drive)

here are the results of dmesg\tail

```
dmesg|tail
[  177.108786] Descriptor sense data with sense descriptors (in hex):
[  177.108789]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  177.108799]         3b 31 58 76 
[  177.108803] sd 1:0:1:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  177.108809] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 3b 31 58 60 00 01 00 00
[  177.108819] end_request: I/O error, dev sdb, sector 993089654
[  177.108835] ata2: EH complete
[  177.108852] JBD: Failed to read block at offset 275
[  177.108855] JBD: recovery failed
[  177.108857] EXT4-fs (sdb9): error loading journal

```

even being able to view the contents of /home for a very short while would help immensely since most of my data is available on the web, but and exact list only exists on /home.

---

