---
title: "boot folder full"
date: 2012-09-18
forum: General Help
---

### Post by zozio32 on 2012-09-18
Hi,

I am running Ubuntu 11.10 on an external HD.  All good here most of the time, just darktable crashing once in a while.

However, my boot directory is full.   It's full of files such as:
[LIST]
[*]abi-3.0.0-12-generic
[*]config-3.0.0-16-generic-pae
[*]or vmlinuz-3.0.0-15-generic-pae
[/LIST]

so first question, can I delete these files?
and second question, how can I do it?  (I have no right, even in the terminal after applying the sudo command, to remove them)

thanks in advance

---

### Post by jerrrys on 2012-09-18
UbuntuTweak makes it easy

[http://www.ubuntugeek.com/how-to-remove-the-old-kernel-versions-from-ubuntu-using-ubuntu-tweak.html](http://www.ubuntugeek.com/how-to-remove-the-old-kernel-versions-from-ubuntu-using-ubuntu-tweak.html)

[http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html)

---

### Post by oldfred on 2012-09-18
I use synaptic so I can see all the kernels in order and keep current and next most current that worked so I have an alternative, just in case.

Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)


HOWTO: Remove Older Kernels via GUI (or CLI)
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

This is older, I have not used tweak.
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by zozio32 on 2012-09-18
Thanks for these answers.

With Ubuntu tweak, I now have the proper path that I can copy in the file browser on top of solving my problem

---

### Post by jerrrys on 2012-09-18
Yes, the solving part :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

