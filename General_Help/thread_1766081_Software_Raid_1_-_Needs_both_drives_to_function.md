---
title: "Software Raid 1 - Needs both drives to function?"
date: 2011-05-23
forum: General Help
---

### Post by Roasted on 2011-05-23
I set up RAID1 with a spare box I have. It's running 4gb flash drive for Ubuntu 11.04 OS and I have MDADM running on 2x500gb SATA drives in RAID1 format. I set this up using the alternate install CD.

The issue is when I go to test the array. It's fully sync'd and has about 5gb of random data on it. If I power off, unplug 1 of the drives, and power back up, the entire array fails to mount. This is true if I repeat the same steps but with the other drive instead.

If I plug in both drives and power up, I'm in good shape.

What gives? I thought RAID1 was okay with 1 drive?

---

### Post by tgalati4 on 2011-05-24
Since you are using software RAID, I presume that mdadm must see the drives at boot (sudo fdisk -l).  This is part of hardware enumeration.  The kernel has to know what devices are attached to it.  If a drive fails during an uptime session, the drive is still mounted and enumerated, it just doesn't work anymore--I/O waits, Drive-Not-Ready, or some other error.  Then mdadm can continue to run in degraded mode.

If you pull the plug on the drive, during boot up, there is one less drive that gets enumerated and mdadm will get confused.  If you want hotswap RAID, then you will need a battery-backed, hardware RAID card that specifically supports hotswap.  I don't think mdadm can support hotswap or missing drives--only enumerated drives that fail during service.

---

### Post by Roasted on 2011-05-24
Ah okay, I understand. It just confused me as an official Ubuntu how-to guide said to check your raid and unplug one drive and see what happens.

Perhaps I misread and they were suggesting to unplug a drive while it's running (ehh) or maybe it's just old instructions that don't apply anymore. I did see something about 8.10 noted in the instructions.

Nonetheless, they still worked for me, I was just super confused on why my array wasn't working. But if it will continue to work when in degraded mode, if one fails when it's running, then it'll do the job I want it to.

Is there a way to tag my email in it to get an email if a drive fails?

EDIT - For the record, is this an Ubuntu thing or a Linux thing? Would Debian work the same way?

---

### Post by tgalati4 on 2011-05-24
For email alerts, install smartmontools:

sudo apt-get install smartmontools

You can set it up to send you an email whenever a SMART parameter on a drive goes bad.  This gives you a warning before actual drive failure.  This is helpful in ~2/3 of drive failures.  The other 1/3 are spontaneous and without notice.

I don't know if mdadm has an email facility.  You could write a cron script to check the status of the array every 1/2 hour or every hour depending on your needs.

I think testing the drive under mdadm means unplug the data cable to the drive (with the machine open) and it still powered up.  That will break the data-connectivity, but not upset the drive controller too much.  Watch for wall messages that describe degraded operation.  Then plug the drive back in and watch for repair messages.

I have hardware RAID on my servers so I don't use mdadm.  Sorry I can't help more.

---

### Post by Roasted on 2011-05-25
Are these terminal programs? I tried to find them but couldn't, and even tried to run them from terminal and still didn't get anywhere...

---

### Post by Roasted on 2011-05-25
New question - let's say my computer blows up. My actual physical computer blows up but I still have access to 1 (or maybe both) of the drives in the raid1 array. How could I access the data on these drives from a recovery standpoint? Could I use just one drive through a usb adapter to connect to my laptop and see what data is there? Or do I need both drives present with the array setup for it to function and be readable?

EDIT - also, when I tested my array earlier by disconnecting a SATA cable on a running system, it indeed took the drive off of the /proc/mdstat listing. Okay fine. I plug it back in... nothing happens...

Somebody in the IRC channel told me to run sudo mdadm -a /dev/md0 /dev/sdb1, which md0 being my array and sdb1 being my drive I disconnected. Okay, fine. The user told me -a was the same as --assemble, which made sense to me that --assemble would = assembling the array by adding a drive to it.

When I did a man mdadm on it, -a isn't assemble. -A is assemble...

I read through the listing of -a and to be quite honest, I have no fricken idea what they were talking about in the -a section. -a is evidently --auto. Okay, fine. What does --auto accomplish? How does -a and -A compare? 



EDIT II:

It also seems -a is listed underneath create, build, or grow. The thing is, I'm not creating, building, or growing. At least I didn't think so. So in this case, -a means one thing, whereas -a I used in my command means another. In my case, I suppose I was in manage mode, and under manage mode -a means --add. Whereas -a under create/build/grow is --auto. **_So the big question - how can a user differentiate manage mode versus create/build/grow mode._**

So I did some more reading... and as I was searching through the man page I found:

```

 -a, --add
              hot-add listed devices.  If a device appears  to  have  recently
              been  part  of the array (possibly it failed or was removed) the
              device is re-added as describe in the next point.  If that fails
              or  the  device was never part of the array, the device is added
              as a hot-spare.  If the array is degraded, it  will  immediately
              start to rebuild data onto that spare.

              Note  that this and the following options are only meaningful 
```

Bingo. So that DOES line up to what is on the Ubuntu wiki, which uses --add instead of -a that I had used:

```

3. Add a Disk to an Array

$ sudo mdadm --add /dev/md0 /dev/sda1
Where /dev/md0 is the array device and /dev/sda is the new disk.
Note: This is not the same as "growing" the array!

```

Well... this has been quite a learning experience. Moral of the story, read the damn man pages, even if they're 1800 lines long! Lots of good info I just read about through my quick skim of mdadm's man page...

---

### Post by Roasted on 2011-05-26
edit - found the answer. I was trying to remove and re-add a drive to the array and I was using /dev/md127p1, which is the device listing for my array when I do a sudo fdisk -l. Turns out I was supposed to use /dev/md0 instead. Worked fine and now it's recovering. Good deal!

---

