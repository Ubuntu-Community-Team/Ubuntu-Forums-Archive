---
title: "Dell mini 910 disk space"
date: 2010-02-10
forum: General Help
---

### Post by Howardfish on 2010-02-10
Firstly may I say I am new to this forum and apologise if someone else has already asked this question but I cant find it. I have a Dell 910 mini Inspiron 910 and like others keeep getting the disk useage warning. The disk is an 8mb flash disk. This has become full by updates and is a real pain.
Q1 can you link an SD card to act as operating memory or is this just for storage?
Q2 If not what is the cheapest and easiest way to upgrade the memory?

Many thanks for any help you can offer

---

### Post by Brandon Williams on 2010-02-10
I'm not certain what the questions about memory have to do wtih the disk utilization problem. The system needs more disk space for the package files, not more memory. Perhaps you're think of the flash disk as if it were memory, but it isn't memory from the system's point-of-view.

An SD card _could_ be used to add disk space such that it becomes possible to complete an update. The first thing you want to do is figure out where all of your disk space is going, though. Is it really used up due to updates? Use du to figure out how much space is being used by downloaded packages. Here's an example from my mini 9 with an 8MB flash.
```
$ du /var/cache/apt/
4	/var/cache/apt/archives/partial
46700	/var/cache/apt/archives
72924	/var/cache/apt/
```

From the output, I can see that there are 46,700KB worth of packages in the apt archives ... not too many. These packages will stick around until the cache is cleaned, so over time they can build up. Running 'sudo apt-get clean' will delete all of the old packages from software that you've already installed. This will only be helpful if there is a _lot_ of space in use in /var/cache/apt/archives/.

If du indicates that you aren't using a lot of space in /var/cache/apt/archives/, then you want to figure out where the space has gone. Run these du command:
```
$ du -s / 2>/dev/null
3175924	/
$ du -s /* 2>/dev/null
5460	/bin
16464	/boot
0	/cdrom
268	/dev
8356	/etc
773124	/home
0	/initrd.img
115776	/lib
16	/lost+found
8	/media
4	/mnt
148404	/opt
0	/proc
4	/root
7632	/sbin
4	/selinux
200	/srv
0	/sys
28	/tmp
1879916	/usr
220256	/var
0	/vmlinuz
```

The output of the first command indicates that my entire system is only using about 3GB of disk space. The output of the second command indicates that /usr and /home are the only directories using enough space (1.9GB and 0.8GB respectively) that it might be helpful to clean them up if I were running short on space, which I am not.

So, is /var/cache/apt/archives the real problem? If so, did running 'sudo apt-get clean' resolve the issue? If /var/cache/apt/archives is not the problem, which directory is eating up all your space? Is it one from which files can be moved to an SD card temporarily (or permanently) in order to allow you to complete the update?

---

