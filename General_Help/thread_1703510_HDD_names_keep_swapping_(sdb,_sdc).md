---
title: "HDD names keep swapping (sdb, sdc)"
date: 2011-03-09
forum: General Help
---

### Post by VanCardboardbox on 2011-03-09
The hdd that my system boots from is named "sdb". But sometimes it's named "sdc". It changes from boot to boot. There are four hdds in this desktop and my boot disk keeps swapping names with a data disk (sdb and sdc). No raid. Never affects the other two disks. 

I am running Ubuntu 10.10, but this problem began when I was a running 10.04.  It was a brand new build at that time, which is no doubt of some importance.

---

### Post by tredegar on 2011-03-09
You should try mounting your disks by their UUIDs, not **/dev/sd*xn***

UUIDs do not change, device allocations can.
Here are two equivalent lines in **/etc/fstab**.

Mount by UUID```
# / was on /dev/sda8 during installation
UUID=22cdc46f-a6e4-43c6-ac42-9046e5fc5372  /               ext4    errors=remount-ro 0       1
```

Mount by device name:
```
/dev/sda8  /               ext4    errors=remount-ro 0       1
```

Find your partition's UUIDs with ```
ls -l /dev/disk/by-uuid
```
Edit your fstab to use UUIDs instead of device names.
Reboot, and all should be well.

Best wishes.

---

### Post by VanCardboardbox on 2011-03-09
Thanks for your reply.

I already use UUIDs in fstab, and did so back when 10.04 was installed. The swapping does not affect performance of the OS (though there is a part on the data drive that I have to check each time I mount it manually).

Even so I would like to know what could be causing it. Don't like that the box is doing something mysterious, beyond my control!

---

### Post by JKyleOKC on 2011-03-09
Starting a couple of years ago, all versions of Ubuntu switched from the traditional sequential boot-up process to an event-driven process called "upstart" that allows different parts of the boot routines to execute at the same time, rather than following strict sequence. The upstart approach does have interlocks that are supposed to prevent race conditions, but parallel processing can sometimes introduce quirks that make it look as if the interlocks are not always working.

The "a, b, c" letters are assigned to drives in the sequence in which the drives are detected by the search algorithms. If one drive is slightly faster than another, although both are within tolerance, it's possible for one to respond first at times, but second at other times, and when that happens, the letters will switch around. This unreliability of the letter assignment is specifically why the use of UUID in fstab and in the grub configuration was introduced. It was always there, but only became frequent enough to be noticed with the parallel processing came into use -- a latency variation of only a microsecond or two can make it happen!

If it really bothers you, look into the "udev" functions. These can re-assign ID letters to things based on other information. I use it to set up my network interfaces based on the MAC of each card; you might be able to use it to assign drive names based on the UUID or the disk label, to force consistency. However I'm not certain whether udev will still be around in future versions...

---

### Post by lithopsian on 2011-03-09
Its a race!  Which disk will win today?  You could sell tickets :)

---

### Post by VanCardboardbox on 2011-03-09
Thanks, JKyleOKC. This seems a very likely culprit. I should keep a log to determine who is winning most of the races! 

I may look into udev, but as I said, the problem doesn't really impact the system's performance. I'm just content to know why its behaving this way. 

Cheers.

---

