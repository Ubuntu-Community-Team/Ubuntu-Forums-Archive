---
title: "Disconnecting drives, fails all mounts?"
date: 2011-06-15
forum: General Help
---

### Post by asd2 on 2011-06-15
Hi!

I run a ubuntu 10.10 server with a couple of harddrives attached, 1 system, 2 small storage, 2 large storage drives in software raid1.

I try to disconnect the 2 smaller storage drives as they are now obsolete and I erase their corresponding lines in fstab and reboot.

This results in a couple of error messages that crypto_something failed and server_swap entries failed to mount with the option to skip mounting with "s". To my knowledge I haven't assigned any swap spaces to the drives now disconnected.

Also my md0 mount point with the raided drives fails to mount although they are connected.

Reconnecting the two unused and according to fstab not mounted disks fixes the issue.

Is there anything I can do to solve this?

ps. sorry for the lack of logs and such

thx in advance

/

---

