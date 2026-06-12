---
title: "Cannot find external drive! NTFS!"
date: 2011-02-23
forum: General Help
---

### Post by Engammalsko on 2011-02-23
Please help me with mounting my NTFS drives from my external hdd.
I had one ntfs, and one wbfs (nintendo wii).

But the wbfs didn't work and corrupted almost my whole drive (strange because the wbfs has worked for 4 month).

Well, I just need to re-download all my games...

But the strange thing is. I formated both partitions extern1 and extern2 to ntfs. And could still just find extern1. So I thaught (very stupid) if I unmaunt extern1 maybe I will se both partitions as one drive...

Which I didn't. And now I can't find anything from my external drive. Please help. What should I install? Which commands shall I use?

I have TeamViewer if anyone can help me there. Please I need help real quick.

Edit: I have Ubuntu 10.10 and it mounted automatically before (only extern1).

---

### Post by Engammalsko on 2011-02-24
bump

---

### Post by seawolf167 on 2011-02-24
Can you run the following command so we can see a list of your plugged in drives and their partitions

```
sudo fdisk -l
```

---

### Post by Engammalsko on 2011-02-26
I have done that many times... But I think I know the problem...

I will try to plug in my drive direct with a sata cable to a stationary computer and see if the HDD works.

The thing is, Ubuntu and XP doesn't find the drive. Not in my computer, my math teacher's computer nor my wii.

But the lamp is flashing blue and you can hear the usb sound thingy in xp when plugin it in/out.

So, if the HDD works in the stationary computer I guess theres something wrong with the dock station?

But something is weird... I unmounted the drive in Ubuntu... And since then it doesn't work on any computer... Could Ubuntu possibly destroy the drive? :s

---

### Post by seawolf167 on 2011-02-26
> **Engammalsko said:**
> Ubuntu and XP doesn't find the drive. Not in my computer, my math teacher's computer nor my wii.

If no computer is able to recognize the drive (of multiple different OS's too) - it's probably a hardware failure.

If the drive is plugged in to your computer, the two commands below will show the drive regardless of format, partitioning, etc. If they are not showing you your drive, I would highly suspect a hardware failure. 

```
sudo lshw -class disk
sudo fdisk -l
```

---

### Post by Engammalsko on 2011-02-26
No I only have: Disk /dev/sda: 160,0 GB

I should have something in style of...
Disk /dev/sda: 160,0 GB
Disk /dev/sdb: 1000,0 GB

---

