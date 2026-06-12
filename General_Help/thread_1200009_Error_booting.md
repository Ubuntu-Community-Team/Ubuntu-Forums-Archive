---
title: "Error booting"
date: 2009-06-29
forum: General Help
---

### Post by Inevitable Glitch on 2009-06-29
I'm running Ubuntu 9.04 on a Dell Latitude D410 that has an older 8GB SSD.  Occasionally I've had problems where during boot it would make me run a manual fsck and push (y) a whole bunch of times.  It's always worked fine after that. Yesterday it did that to me again, same as usual except that, now it won't boot into the gui.  It gives me this:

```
Boot from (hd0,1) ext3 010e334d-56e7-9b0f-e307cc1d4a9e
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/ecb96d83-4f2c-4880-af10-b7ad9dba02c3) = dev(8,1)
kinit: trying to resume from /dev/disk/by-uuid/ecb96d83-4f2c-4880-af10-b7ad9dba02c3
kinit: No resume image, doing normal boot...
mount: mounting /proc on /root/proc failed: Input/output error

Ubuntu 9.04 ubuntu-d410 tty1

ubuntu-d410 login: _
```

Any help would be appreciated.  I have files on the hard drive I need, so at the very least I need advice on getting them off so that I can reinstall.  If you need more info just ask and let me know how to get it, I'll be glad to.  I'm not exactly computer illiterate, but I'm no wiz and I'm fairly new to Ubuntu so bear with me a little.

Again, thanks for any help.

---

### Post by Inevitable Glitch on 2009-07-01
Still no progress..., I need some help troubleshooting here as I have no idea where to begin, I'm not familiar with Ubuntu and it's commands enough to do this on my own.  I am to the point of just trying to rescue my files and reformat.  Any help would be greatly appreciated.

---

### Post by Inevitable Glitch on 2009-07-01
Well, thanks for all the help guys.

After a couple days of no responses I got on IRC and somebody calling himself "linuxguy2009" proved quite helpful (Many thanks man) and after messing around with it for a while I decided to just do a fresh install and go from there.

---

