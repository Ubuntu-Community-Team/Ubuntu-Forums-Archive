---
title: "/proc/ toturial"
date: 2011-10-25
forum: General Help
---

### Post by saltcushy on 2011-10-25
Plese send post easy digestible for me
I found answer probable but i don't know how use it.
[http://oclug.on.ca/archives/oclug/2003-January/027082.html](http://oclug.on.ca/archives/oclug/2003-January/027082.html)
If autor wroute about> Booting by hand using grubso Why doesn't work command mount in gub menu.
I see step like:
```
init-2.03# mount -t proc none /proc
init-2.03# mount -o remount,rw /
init-2.03# mount /usr
init-2.03# vi /etc/fstab
```
Next He wrote about a save? what's this?(work ony ctr+X, right?)
Then I see lines "very important"(up lines are not important?)
> init-2.03# umount /usr
init-2.03# mount -o remount,ro /
init-2.03# umount /proc

> init-<bash-version>#????
by the way I apologize for my English

---

### Post by blueridgedog on 2011-10-25
Perhaps you can describe what you are trying to do or what the problem is you are trying to solve?  It may be that your system can better be repaired with the environment you get when booting off of a LiveCD.

---

### Post by saltcushy on 2011-10-26
I wanna repair system, because when linked two partition in Gpated after system crashed,(changed its position system)
In live CD for command  update-grub, to lack /proc/
> I have no name!@ubuntu:/# update-grub
Generating grub.cfg ...
grep: /proc/mounts: No such file or directory
grep: /proc/swaps: No such file or directory
by the way, nothing commands can't fix ip up, I  tried many commends

---

