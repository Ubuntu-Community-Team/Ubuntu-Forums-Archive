---
title: "How to check disks and general health of Ubuntu after hard reset?"
date: 2011-03-02
forum: General Help
---

### Post by Mickpunt on 2011-03-02
Hi,

I have recently had to perform several hard resets on my machine running ubuntu 10. The freezes are still being caused by XBMC (taking 100% CPU), see [http://forum.xbmc.org/showthread.php?t=95139](http://forum.xbmc.org/showthread.php?t=95139).

I hate doing a hard reset but I tried lots and lots of alternatives to avoid doing a reset.

From a SSH session to my ubuntu machine I tried sudo reboot, sudo kill -9 on XMBC process, tried the direct kernel approach: 
ALT + SysReq + r (This stands for Raw keyboard mode)
ALT + SysReq + s (This syncs the disk)
ALT + SysReq + e (This terminates all processes)
ALT + SysReq + i (Kill&#8217;s all processes that weren&#8217;t terminated nicely.)
ALT + SysReq + u (Remounts all filesystems as read only.)
ALT + SysReq + b (Reboots.)

Tried Ctrl-Alt-F8 to start a terminal and kill XBMC or at least reboot. But nothing works... so yeah wat else but to switch the computer off?

Anyway my question, I'm afraid the OS or the disks might have been damaged. Is there anyway to check this in Ubuntu? Does Ubuntu do any kind of self-repair?

Thanks!

---

### Post by TeoBigusGeekus on 2011-03-02
Boot up with a live cd and do
```
sudo fsck /dev/sdwhatever
```
to all your partitions.

---

### Post by Smart Viking on 2011-03-02
If you use ext3 or ext4(which you probably are), then you are using a journal file system. This basically means that it will handle hard resets much better, so there is not really so much to be afraid of. If it boots up and runs fine then it probably have fixed everything itself.

---

### Post by jerome1232 on 2011-03-02
fsck should get automatically run during startup after an unclean shutdown.

You can check when it was last checked with tune2fs

```
sudo tune2fs -l /dev/devicename | grep "Last checked"
```

see what the check interval is (meaning how often it will be checked

```
sudo tune2fs -l /dev/devicename | grep "Check interval"
```

change the interval to one week (change the numbers and use d/m/w to set day/months/weeks respectivly)
```
sudo tune2fs -i 1w /dev/devicename
```

Change the time last check (so you can force a check at next boot by setting it to like 6 months ago)
```
sudo tune2fs -T YYYYMMDD
```

---

### Post by Mickpunt on 2011-03-02
Ok smart viking, good to know about the benefits of [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system"). Indeed I am using both ext3 and ext4.

Here's how my fstab looks:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c538eb58-c03a-460f-8d5a-dab54a4a3d24 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=ac2edcd1-a4b8-4dff-8b2c-88e888d24347 none            swap    sw              0       0

# Media sda3
UUID=9652d076-d2a1-48bc-8f0a-0d7862f3f6e0       /mnt/media      ext3    defaults  0  0

# Extra disk
UUID=d00a737a-6641-4c94-86be-92eda5044e7e       /mnt/stuff      ext4    defaults        0       0
# RAID
/dev/md0        /mnt/raid       ext4    defaults        0       0

```

Will running sudo fsck /dev/sdwhatever from a live CD - as TeoBigusGeekus suggests - not hurt my RAID partition?

Thanks for the help guys!

---

### Post by Mickpunt on 2011-03-02
Ok, intervals were all set to 6 months. Changed them all to 2 weeks.

Thanks Jerome

---

