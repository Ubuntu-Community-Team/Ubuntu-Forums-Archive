---
title: "A Couple of Random Problems"
date: 2011-03-16
forum: General Help
---

### Post by christopher2405 on 2011-03-16
I installed Ubuntu 10.10 a couple of days ago as half of a dual-boot system (the other half being my preinstalled Windows 7 Home Premium). Both operating systems are 64-bit, and all hardware is working fine, with the 320GB hard drive being partitioned as follows:

[LIST=1]
[*]OEM partition (no label)
[*]Windows Recovery (RECOVERY)
[*]Windows 7 (OS)
[*]Ubuntu boot (/boot/)
[*]Swap
[*]Home (/home/)
[/LIST]
I set up Firefox so that it was using the same profile as Windows, stored on OS. This worked fine, but I suddenly lost all of my bookmarks when I went back on Firefox later on in the day. This wasn't too bad, as I don't use bookmarks all that much, but then Firefox started playing up.

I'd try to start Firefox as soon as the system booted, but I would get the "Firefox is already running, but isn't responding..." message, but there was no Firefox process running. This problem was overcome by mounting the OS drive, so I presumed that was where the problem was. This led me to set up the computer such that the OS partition is mounted on startup, but I am still getting the Firefox is already running message. If I use Firefox with a profile stored on /home/, it works just fine.

Another thing is that I keep getting random "Access denied" or similar messages, such as when I right click on OS and try to unmount (I still haven't got around this) or when I was trying to install a new package, and was told that apt-get was already running (which it wasn't).

Any help would be much appreciated, thanks :)

EDIT: I forgot to mention, I have 100GB of unallocated space, which I was going to partition as NTFS and use as a link between the operating systems, where I can store my documents, music, etc. However, my hard drive has the maximum number of partitions, so I want to get rid of swap, replacing it with a swap file. How can I do this? I tried with the Ubuntu partition manager, but it wouldn't let me as swap is sda5 and home is sda6 (or something like that)

---

### Post by christopher2405 on 2011-03-19
Bump.

---

### Post by christopher2405 on 2011-03-23
Bump.

---

