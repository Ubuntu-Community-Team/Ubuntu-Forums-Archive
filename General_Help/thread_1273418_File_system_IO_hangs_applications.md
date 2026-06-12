---
title: "File system I/O hangs applications"
date: 2009-09-23
forum: General Help
---

### Post by sgreimer on 2009-09-23
I've done some preliminary research and testing before writing this post but so far have been unable to find a solution.

The problem is this: When doing any activity involving large amounts of file system access - local/network/usb file copies, using virtual machines etc - my applications slow to a crawl and usually become unresponsive. The file copies also seem to surge in speed.

I have switched my IO scheduler to cfq which made no difference. I also ran hdparm on both of my harddrives but the test seems to be fine.

[FONT="Courier New"]/dev/sda:
 Timing cached reads:   1276 MB in  2.00 seconds = 637.54 MB/sec
 Timing buffered disk reads:  170 MB in  3.02 seconds =  56.37 MB/sec

/dev/sdb:
 Timing cached reads:   1286 MB in  2.00 seconds = 642.25 MB/sec
 Timing buffered disk reads:  240 MB in  3.01 seconds =  79.81 MB/sec[/FONT]

fdisk on both drives return no errors.

This problem started in the last couple weeks but I can't pinpoint the exact time or anything that would have triggered this. 

I don't know where to look next.
Oh, and I'm using 8.04 and my system is up to date.

---

### Post by ibuclaw on 2009-09-23
Heavy File I/O in Virtual Machines?

Quick two questions for you:
1) How big are the Virtual Hard Disk(s)?
2) How many extents are they in?

You can find the answer by using the following utilities:
1)
```
du -h ~/.VirtualBox/HardDisks/*
```
2)
```
sudo filefrag ~/.VirtualBox/HardDisks/*
```
I assume you use VBox, you may be using kvm, or vmware...

Regards
Iain

---

### Post by sgreimer on 2009-09-23
Most of the VM files have only 1 extent, a few have more. I think the VM mention was misleading. The problem isn't directly related to my issue. It's just one of the times I notice the problem and it's usually only while loading. Once they're running it's fine, unless I am copying files.

The key is that any activity that accesses the file system aggressively causes applications to hang even though CPU usage is usually < 10%

---

### Post by dcstar on 2009-09-25
> **sgreimer said:**
> 
.........
This problem started in the last couple weeks but I can't pinpoint the exact time or anything that would have triggered this. 

I don't know where to look next.
Oh, and I'm using 8.04 and my system is up to date.

And how much free space do you have in your filesystems?

---

### Post by sgreimer on 2009-09-25
sda1 = 51%
sda2 = 16%

Nothing that should cause this.

---

### Post by sgreimer on 2009-09-25
I found the problem. It was a bad disk. For some reason, hdparm and fdisk didn't find any issues but if I remove it from the picture everything is ok.

---

