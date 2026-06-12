---
title: "some basic questions about ubuntu and linux ?"
date: 2012-03-25
forum: General Help
---

### Post by zzzubu on 2012-03-25
1. what is the recovery mode when ubuntu boot up ?
2. is the "root" folder the parrent folder of "dev" "home" "boot" or sabling folder ?
3. what is this development "dev/loop2" ?
4. can i install a ubuntu OS without mounting the "boot" folder ?
5. in terminal  how to set ubuntu to login automatically ?
6. which mount points should must be setted when installation ?

sorry for my poor english, i hope you can understand what i have said.

---

### Post by oldfred on 2012-03-26
Welcome to the forums.

The recovery mode is if you have problems. It now gives several choices on some auto repairs or letting you get to a terminal if gui/video does not work so you can run updates or repairs yourself.

/ (root) is the top level in Linux.
Explaination of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)
Some real old history:
[http://lists.busybox.net/pipermail/busybox/2010-December/074114.html](http://lists.busybox.net/pipermail/busybox/2010-December/074114.html)

/boot is one of the required folders. Desktops usually do not need that in a separate partition unless you have an old system with the 137GB BIOS boot limit and then if / is fully inside the 137GB limit you still do not need a separate /boot.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

As part of the install you can specify whether to login on boot or not. You still need password to use sudo to make any system changes, updates etc.
Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

Default install is just / (root) and swap. But normally we suggest a separate /home. Often best to partition in advance.
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Very detailed instructions with screenshots:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Not sure on you question of dev/loop2? Is this from liveCD or USB?

---

