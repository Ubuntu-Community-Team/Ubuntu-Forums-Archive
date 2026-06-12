---
title: "Ubuntu Crashed, won't boot. Recovery not helping."
date: 2010-12-29
forum: General Help
---

### Post by Smartflight on 2010-12-29
I came over from my friend's and turned the laptop on, and went to drink water. The battery backup is about a minute (yes, consider it dead). Came back, it was logging in at that moment, and bam, it shut down. At first, I thought it over-heated, which made no sense. Checked the temperature and it was cold. Next, I checked if I had switched the plug on or not- nope, I hadn't.

Nevermind. I went to the market to feed myself, came back, turned it on, and it won't boot. A month ago, I had the same issue, and tried everything you can think of (I mean it) and finally had to reinstall Ubuntu via my 512kbps net connetcion, and no backups. It was annoying, but since I had a week without my laptop, finally having one made me happy.

This time, the error is just the same. I tried recovery mode (Ubuntu, with Linux 2.6.35-23-generic)and it tries to do something a few times, after which it comes to this: (posting whatever is on-screen)

```

[2.307647] Console: switching to colour frame buffer device 160x50
[2.317581] fb0: radeomdrmfb frame buffer device
[2.317653] drm: registered panic notifier
[2.317721] Slow work thread pool: Starting up
[2.317897] Slow work thread pool: Ready
[2.317967] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
No init found. Try passing init= bootarg.


Busybox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) help
Built-in commands:
. : [ alias break cd chdir command continue echo eval exec exit
export false getopts hash help let local printf pwd read readonly
return set shift source test times trap true type ulimit umask
unalias unset wait [ [[ ash awk basename cat chmod chroot chvt
clear cmp cp cut deallocvt df dnsdomainname du dumpkmap echo
egrep env expr false fbset fdflush fgrep find grep gunzip gzip
hostname ifconfig ip kill ln loadfont loadkmap ls mkdir mkfifo
mknod mkswap mktemp more mount mv openvt pidof printf ps pwd
readlink reset rm rmdir sed setkeycodes sh sleep sort stat static-sh
stty sync tail tee test touch tr tune tty umount uname uniq wc
wget yes zcat

(initramfs) _


```

Before this, it clears up what recovery mode was trying to do. It said /dev/sda5 filesystem needed repairing. It tried to do that, and something like at3: in front of almost every line. There was also a "device not ready" in each of its try.

This is frustrating.
CD/DVDs will not work.
Pen drives won't.
PXE booting is tedious.
Net install without backup- not happening.

---

