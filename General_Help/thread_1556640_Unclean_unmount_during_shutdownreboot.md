---
title: "Unclean unmount during shutdown/reboot"
date: 2010-08-19
forum: General Help
---

### Post by tekkenlord on 2010-08-19
I am using Kubuntu 10.04 64-bit and have disabled plymouth in order to see what exactly is going on during
startup/shutdown.

Almost everytime I shutdown/reboot my computer I see the following msg:

[...]
Unmounting weak filesystems...
mount :/ is busy
[...]

and then the computer shuts down.

On startup, I receive the msg that the drive (sda1 in my case) needs to be recovered:

EXT3-fs (sda1): INFO: recovery required on readonly filesystem
[...]
EXT3-fs (sda1): recovery complete


I found a similar report here:

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

but applies to the 10.10 release.

I am worried that this can cause data corruption or loss. Please also note that many users may be unaware of the problem since most have plymouth enabled (therefore there are no msgs appearing during shutdown)

Is anybody else experiencing this? Any suggestions are appreciated. Thanks!

---

