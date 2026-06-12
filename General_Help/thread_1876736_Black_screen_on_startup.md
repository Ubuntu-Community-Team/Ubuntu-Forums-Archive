---
title: "Black screen on startup"
date: 2011-11-06
forum: General Help
---

### Post by Findecanor on 2011-11-06
I have an installation of Ubuntu 10.04 LTS.

So I had run Computer Janitor from the menu... I had had this misplaced trust in humanity that had led me to believe that people who made it and put it there know how to think. If running it would foul up my system, then it would not be the first item in the menu and it would give me a little bit of warning about how dangerously inaccurate it is at selecting "unnecessary" packages before allowing me to continue ...

Anyway ...

The result is that I get a black screen on startup when the login dialog is supposed to appear.
<Ctrl>-<Alt>-<F*n*> does not give me a console.

I get a black screen after boot even when I had booted into recovery mode!

I have been able to boot the installation CD and mount the file system.
I guess that the action that caused my system to be unusable might be in dpkg's log:
```
$ less var/log/dpkg.log | grep remove
2011-11-06 21:25:11 startup packages remove
2011-11-06 21:25:16 remove frontdesign 4.1.1-1 4.1.1-1
2011-11-06 21:25:18 remove libavutil49 4:0.5.1-1ubuntu1.2 4:0.5.1-1ubuntu1.2
2011-11-06 21:25:19 remove libmatroska0 0.8.1-1.1 0.8.1-1.1
2011-11-06 21:25:20 remove libebml0 0.7.7-3.1 0.7.7-3.1
2011-11-06 21:25:20 remove libx264-85 2:0.85.1448+git1a6d32-4 2:0.85.1448+git1a6d32-4
2011-11-06 21:25:20 remove nvidia-current 195.36.24-0ubuntu1~10.04.1 195.36.24-0ubuntu1~10.04.1
2011-11-06 21:25:40 update-alternatives: run with --remove gl_conf /usr/lib/nvidia-current/ld.so.conf
2011-11-06 21:25:41 remove vim-runtime 2:7.2.330-1ubuntu3 2:7.2.330-1ubuntu3
2011-11-06 21:25:44 remove fortunes-min 1:1.99.1-3.1ubuntu4 1:1.99.1-3.1ubuntu4
2011-11-06 21:25:44 remove fortune-mod 1:1.99.1-3.1ubuntu4 1:1.99.1-3.1ubuntu4
2011-11-06 21:25:45 remove librecode0 3.6-17 3.6-17
2011-11-06 21:29:41 startup packages remove
2011-11-06 21:29:42 remove dkms 2.1.1.2-2ubuntu1 2.1.1.2-2ubuntu1
2011-11-06 21:29:43 remove fakeroot 1.14.4-1ubuntu1 1.14.4-1ubuntu1
2011-11-06 21:29:43 update-alternatives: run with --remove fakeroot /usr/bin/fakeroot-sysv
2011-11-06 21:29:43 update-alternatives: run with --remove fakeroot /usr/bin/fakeroot-tcp
2011-11-06 21:29:43 update-alternatives: link group fakeroot fully removed
2011-11-06 21:29:44 remove linux-headers-2.6.32-21-generic 2.6.32-21.32 2.6.32-21.32
2011-11-06 21:29:47 remove linux-headers-2.6.32-21 2.6.32-21.32 2.6.32-21.32
2011-11-06 21:29:50 remove nvidia-settings 195.36.08-0ubuntu2 195.36.08-0ubuntu2
2011-11-06 21:29:51 remove patch 2.6-2ubuntu1 2.6-2ubuntu1

```What could be the best course of action?

Is there a way to re-install the packages, by booting from another install (the installation CD) and installing the packages onto a mounted file system?
I would like to avoid doing a fresh install, if at all possible. I have installed much software from other sources and I have an encrypted home directory.

Thanks in advance for any help
/ Johan

---

### Post by searchfgold6789 on 2011-11-06
Boot from a Live CD.
Open up a terminal.
Type in the following and then proceed to try to recover your system:
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```Replace XX with your hard disk # and partition # for /.
Good luck
 - search

---

### Post by Gremlinzzz on 2011-11-06
most likely a fresh install but this is worth a shot:popcorn:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Peter Parkorr on 2011-11-06
Is this a known problem with Computer Janitor and 10.04, or just unlucky?

---

### Post by Findecanor on 2011-11-08
Thanks guys.

I got back in anyway by booting an older kernel. I can not say why it worked now, while it did not before.

> **Peter Parkorr said:**
> Is this a known problem with Computer Janitor and 10.04, or just unlucky?
From reading random posts about it on this forum.. it has fooled other people before, maybe not to the point of making the system unusable as in my case, but it sure has aggravated some people.

---

