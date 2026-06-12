---
title: "HDD being used all the time"
date: 2012-09-15
forum: General Help
---

### Post by KouDy on 2012-09-15
Hello everyone,
i don't really know what is going on with my second laptop (HP Elitebook 84440p). I have Ubuntu 12.04 installed and updated (not many programs installed). Recently (say, 2 days) i found out that HDD keeps working in strange manner. Even right after boot when the machine is idling (i don't run anything, just start it up) i can see that HDD led goes up for 3-5 seconds, then it goes off for 3-5 seconds, on again, and so on.
I think i need to find out what file is it accessing and perhaps prevent it from doing it.

How do i do this?

---

### Post by squaregoldfish on 2012-09-15
You can install a program called iotop (in the repositories) which is like top for disk usage - it tells you which programs are using the hard disk. That could give you some clues.

Steve.

---

### Post by KouDy on 2012-09-15
Thanks for the hint. I tried looking for iotop (apt-get install iotop) but it seems it does not exist.

---

### Post by squaregoldfish on 2012-09-15
Strange. It's in the universe repository, so it should be available for installation. :confused:

I don't know what to suggest, unless universe is disabled on your system.

Steve.

---

### Post by KouDy on 2012-09-16
I have tried something else tho. I went and booted up Backtrack i have installed paralelly and the problem is there as well. I have a hunch that it's hardware problem, not software...

Connecting HDD to my windows machine is fail as it won't let me access any partitions (only 3 out of 7 and those i don't need to access). I will have to find some checkdisk for Ubuntu.

EDIT : So after pulling HDD out and connecting to windows machine i plugged it back. I went and booted up ubuntu again and ran
```

sudo badblocks -v /dev/sda3 > bad-blocks

```i ran it for all /dev/sda numbers i have (1-8 ) and found 0 errors on any of the partitions.

---

### Post by varunendra on 2012-09-18
> **KouDy said:**
> Connecting HDD to my windows machine is fail as it won't let me access any partitions (only 3 out of 7 and those i don't need to access). I will have to find some checkdisk for Ubuntu...
If the remaining 4 are linux partitions, you can try [ext2fsd]("http://www.ext2fsd.com/") or [ext2ifs]("http://www.fs-driver.org/") to access (even write to) them from windows. However, it is not recommended to let them mount your linux partitions 'permanently' (at win startup) due to security implications. Only use such applications if you really need to. I should also mention that you can't use windows 'chkdsk' on linux partitios even if it is mounted through such applications/drivers (the chkdsk program doesn't understand the filesystem).

As for your issue, try these:

[LIST]
[*]If your laptop's BIOS has these or similar options, 1) enable 'SMART' on the drive and see if it reports some problem (keep it enabled for anyway); and 2) run 'Scan Disk' on your hdd.
[*]Boot from a live cd and use 'fsck' command with -f option on your linux partitions (eg. ***fsck -f /dev/sda1*** , assuming sda1 is a linux partition)
[/LIST]

---

