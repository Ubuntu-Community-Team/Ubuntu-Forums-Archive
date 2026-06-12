---
title: "Working with Ubuntu atrociously slow due to harddisk performance issues!"
date: 2010-04-12
forum: General Help
---

### Post by FnordPerfect on 2010-04-12
Any task that involves loading a bunch of scattered files off the hard disk is terribly slow!

Also, under heavy I/O (e.g. when updating locate database or installing software with apt-get), the performance drops so low I cannot even move my mouse cursor anymore.

I am on Karmic, but this misbehaviour goes back at least 3 releases... actually, I cannot remember anymore whether Ubuntu ever felt fast and responsive to me.
(I was somehow hoping it would be a kernel issue concerning my SATA hard drives
that would somewhen resolve itself, but it never happened.)

So now I am asking for your advice!

CPU:  AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
RAM:  2GB

My Disks are
Western Digital WDC WD7500AACS-00D6B0 (750GB) <- / and /home
Western Digital WDC WD1600AAJS-08PSA0 (160GB) <- swap

Here are some Wall clock "benchmarks" to give you an impression: 

[LIST]
[*] De-installing a package via dpkg -P
	(Reading database... xx%) takes about **50 seconds**

[*] Launching nautilus ~
	**8 seconds** till the window appears
	**5 more seconds** till the content is shown

[*] User switching, going from Gnome to gdm
	I can watch the background image crawling back from swap and drawn to screen *line by line*; akin to Windows 95 on my 486 8MB RAM back in the days


[*] Starting gmrun (which is supposed to be a tiny command launcher) 
takes about **3 seconds** (the first time started)

[*] Clicking the *friggin'* Applications menu
	**2 seconds** till the menu entries show, **ca. 1 seconds** till the icons are loaded
[/LIST]	

If this were 2003 my advice would be to check hdparm whether the correct DMA channel is turned on... however, the raw I/O throughput looks quite good:

```
/dev/sda:
 Timing cached reads:   1784 MB in  2.00 seconds = 891.83 MB/sec
 Timing buffered disk reads:  206 MB in  3.04 seconds =  67.80 MB/sec

/dev/sdb:
 Timing cached reads:   1800 MB in  2.00 seconds = 899.71 MB/sec
 Timing buffered disk reads:  206 MB in  3.01 seconds =  68.46 MB/sec

``` 

My partitions are mounted with these flags

```
/dev/sda1 on / type ext4 (rw,noatime,nodiratime,errors=remount-ro,nobarrier)
/dev/sda2 on /home type ext4 (rw,relatime,nobarrier)
```

As of now I am baffled.
I tried some random kernel parameters, but nothing really helped.
I tried the preload daemon, to no avail.
I tried adding these noatime and nobarrier flags to /etc/fstab, which somewhat improved performance but not much.

I am grateful for any hints!
 ~fab

---

### Post by xir_ on 2010-04-22
id like to confirm im having very similar issues for the last couple of releases.

One thing to check is if ureadahead is eating up ram as this really did a lot of damage to me.


if df -h shows a ureadahead entry try uninstalling it.

---

### Post by DawieS on 2010-04-22
I can confirm that I noticed something similar a few days ago. Normally files are copied at a rate of +50 MB/s between drives on my machine. At the time I was running a few torrents for 2 days, when I attempted to copy a few files to an external SATA drive. The copy went at 6 MB/s, which is slower that copying to an USB flash drive (+8MB/s). I eventually aborted the copy until after a reboot, when it was normal again.

Somehow I now cannot replicate the same situation, and don't know what the cause was, or where to start looking for possible causes.

I am using Karmic 32 bit on a desktop.

---

### Post by yuno.33 on 2010-09-17
i feel like a total beginner here :O

recently i bought a sata harddisk to replace my old pata which infested with bad sectors. after i found out the replaced sector isn't growing i decide to keep the old. thus, my computer run with two hd installed, each has its own ubuntu system. however, some file operations take up too much time, extracting and adding files to archive appear to takes the most (100kb per second when extracting uncompressed tar archive).

after few experiments, here's what i found;

operating files at different partition of the same hard disk takes up so much times. the transfer rate, when copying, hit 1.8 megabyte per second.
operating at the different hard disk appear normal. transfer rate reaches 50+ megabyte per second when writing to sata, or 30+ Mbps when writing to pata.
these two situations appear no matter from whichever hard disk boot.
transfer rate return normal when one of the hard disk unplugged, leaving only one operating.

for people who wish to have 'fake' problem solving, i suggest unplug one of your hard disk. you, unfortunately, have to work with only one hard disk installed.
for people who wish to have real solution, i can't provide and i would like to ask too!

---

