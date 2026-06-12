---
title: "SSD issues and more weirdness!"
date: 2012-08-23
forum: General Help
---

### Post by Lodmot on 2012-08-23
I am in the process of trying to get the desktop computer from hell to work.
The thing was literally conceived from hell, I swear... (Even though I built it..)

Anyway, so I install Ubuntu 12.04 on my system, the regular Live CD kept failing with some kind of I/O errors (I forgot exactly what the error said since it's been like 2 days since I last tried using the regular Live CD with this computer). Then I got the alternative install CD, with the purple DOS-like interface, and from there I was able to install Ubuntu 12.04.

The install process went smoothly, but then I encounter the first oddity that happens at every boot-up. After the GRUB boot menu where you select an OS, the screen goes blank and hangs there for like a minute and thirty seconds, before finally blacking out and then going into the Ubuntu logo, where it speeds up from there. That's odd, because my laptop which also runs on 12.04 has an SSD and boots up literally in 10 seconds! But the desktop from hell here takes like a minute and 30... 

Well anyway, I boot up, and decide to first install all updates, which there are like 400 of since 12.04 was released. It gets pretty far in the update process, but then fails. I've had it succeed before though. It's VERY temper-mental. So then I reboot the computer, it boots back up. And now Terminal doesn't work. When I open a terminal it displays a bunch of random text for a split second, then closes. A TTY session also does this too, but there it just kicks me to the login prompt.

So that's my ordeal..

My custom built system is an ASUS P5NSLI with 4GB of RAM, a Pentium D 3Ghz processor, 64GB SSD, a 400 GB HDD, an AMD Radeon HD 6770 graphics card and a Creative SBLive sound card

So, any ideas anyone? Thanks.

---

### Post by drmrgd on 2012-08-23
No solution, but just a couple quick questions.  How do you have your SSD set up in BIOS (i.e. RAID, AHCI, IDE)?  Are the two drives setup for SSD caching or same variant thereof?  I looked up the specs on the MoBo, and I don't see SSD caching or Intel SRT available on the board, but I could be missing something.  What kind of connection did you use to connect the SSD to the board?

I'm not sure what the problem is exactly, but maybe there is just something a little off with how's it's connected or the protocol being used to access it.

---

### Post by Lodmot on 2012-08-23
Well you know, I did look up on that, and read that ACPI does increase performance on SSD's, but I couldn't find an option for it anywhere in my BIOS. There's a S.M.A.R.T. disk option, but I don't think that's the same thing. My board is pretty old, from like 2007 or 2008 maybe. I have it connected to SATA to the SSD.

---

### Post by oldfred on 2012-08-23
I would look in log files. And see if it reports some error, tries to load something and then just times out or gives up and anything with a very long time between entries.

You can use Log File Viewer. 

There are lots of log files, I look at dmesg first.
 The logs are in /var/log.

---

### Post by drmrgd on 2012-08-23
I'm not totally sure that I'm necessarily on the right track (Fred's log file advice is excellent!).  I'm interpreting this as a general I/O issue, which is why I'm looking at the way your SSD is connected.  It could be something altogether different, though.  

But I had a quick look, and for sure your board does not support AHCI.   Aside from performance issues and not being able to enable TRIM (I'm not  sure you can do it without AHCI support), I'm not sure what other  consequences you'll see.

---

### Post by Lodmot on 2012-08-23
Alright. The dmesg log is insanely huge. I looked through it and noticed some errors like this:

"ata3.00: failed command: READ FPDMA QUEUED
  ata3.00: cmd 60/08:f0:f0:0b:00/00:00:01:00:00/40 tag 30 ncq 4096 in
                   res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
  ata3.00: status: (DRDY)"

Then below that there are some "ata3.00: device reported invalid CHS sector 0" errors.

And below that there's a bunch of "Add. Sense: No additional sense information"

Then I saw those same bunch of errors one more time. And that's pretty much it.

I dunno what any of that means, but it sounds like some kind of disk errors of some sort, because of it mentioning sectors...

I don't know what FPDMA is, or whether it's related.

---

