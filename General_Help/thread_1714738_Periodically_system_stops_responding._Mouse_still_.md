---
title: "Periodically system stops responding. Mouse still moves. How to troubleshoot?"
date: 2011-03-25
forum: General Help
---

### Post by tgm4883 on 2011-03-25
So I've been trying to troubleshoot this for awhile now, but I am not having any luck. 

Motherboard: Gigabyte 965P-DS3 V 2.0
Processor: Intel Core 2 Quad Q6600 (recently updated from a E6300, but it happened there too)
RAM: 2GB
Video Card: Geforce 7300GS
Sound Card: Onboard
Hard Drive 1: 500GB 
Hard Drive 2: 160GB
Ubuntu 10.10 64-bit

The issue is that the machine will stop responding periodically for 1-3 minutes. During this time I can still move the mouse and may be able click on and switch to other windows. During this time, the CPU isn't using any significant amount and my ram isn't maxed out (i'm not swapping either). I've seen this happen when I am doing two tasks.
* When transferring large files from this machine to another
* When loading large video files into handbrake GUI (not using network)

Troubleshooting I've done:
* Memory test. 100% passed
* Switched out power supply
* Upgraded CPU (to the Q6600)
* I haven't seen anything worthwhile in syslog nor messages, but I'm willing to post those here if anyone wants to have a look. 
* Disabled proprietary Nvidia drivers
* I've tested a Debian 6 live disk, and it didn't seem to happen during transfers, but I'd have to install on another hard disk and find out. 

FWIW, I thought I had seen this same issue on 8.04 RC's and it was fixed in final, but it's been so long ago I don't recall.

I've also run iotop when transferring a large file, and I've noticed that it reads a bunch from the disk quickly, then stops reading, then reads a bunch again and so on. During this time my network activity is steadily high, so I think this is probably normal.  

At this point, I'm not sure what else to check. I don't see this on any of my other systems, although besides my work machine (at work), this is my main system. I'm stopping by frys tonight to pick up some more memory (4GB total) and a new gigabit switch (since mine is having some issues of it's own it seems). 

If anyone has any ideas on what else to try it would be greatly appreciated.

---

### Post by nice_like_rice on 2011-03-25
Although I know it's not much help, I wouldn't say it sounds like a hardware problem...

---

### Post by tgm4883 on 2011-03-25
> **nice_like_rice said:**
> Although I know it's not much help, I wouldn't say it sounds like a hardware problem...

Thanks for replying. Yea I don't think it sounds like a hardware problem either. The hardware that I've upgraded so far (CPU) was a planned upgrade. The memory is a planned upgrade as well. I actually had another power supply laying around that I was able to test, as well as a PS tester.

---

### Post by tgm4883 on 2011-03-28
So I replaced my Hard Drive and I haven't gotten the long instances where the system stops responding. I'll occassionally have brief moments where everything will lock up, but this only happens for 1-5 seconds when the system is under heavy load, so likely normal. Not much in the disk utility regarding errors, so I'm unsure how I would have known about this.

---

