---
title: "Can't reboot; amd NFS hangs"
date: 2009-10-10
forum: General Help
---

### Post by yang on 2009-10-10
I can't reboot my system. I just see the following, and then nothing happens. I've entered this several times now.
```
$ sudo reboot
[sudo] password for yang:
$
Broadcast message from yang@harvard.csail.mit.edu
        (/dev/pts/7) at 4:31 ...

The system is going down for reboot NOW!

```
Probably relevant information: my amd-managed NFS mounts have gone haywire, after the NFS/NIS servers (same host) became inaccessible for several hours. I can create fresh new NFS mounts just fine, but the existing ones are not responding (or more precisely, *barely* responding).  E.g., ls on the directories hangs for minutes, and then fails with only some of the subdirectories actually getting listed (albeit in red) and others resulting in "No such file or directory" error messages. I've been waiting for a reboot for half an hour now.

I'm running Ubuntu 9.04 with regular updates. I don't have physical access to the computer, so it's important that I be able to reboot it and not simply shut down. And BTW, if anyone knows how to deal with the hung NFS mounts without rebooting, that'd be good to know as well.

Thanks in advance for any help.

---

### Post by jtappin on 2010-03-29
Probably a bit late now, I saw this while looking for NFS/NIS issues.

From my recollection of similar problems some years back (Debian Sarge era) the only fix for this is to get hold of whoever does have physical access ad get them to press the reset button.

---

### Post by yang on 2010-03-29
That is indeed what we ultimately end up doing every time this comes up. Doesn't come up too often, but it's a real PITA.

---

