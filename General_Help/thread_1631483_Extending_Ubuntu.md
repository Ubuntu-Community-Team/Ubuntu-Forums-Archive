---
title: "Extending Ubuntu"
date: 2010-11-26
forum: General Help
---

### Post by RiThePirate on 2010-11-26
Hey guys, I have Ubuntu 10.10 installed along side of Windows 7 on the same partition. I'm a bit of a noob as I have only recently gotten serious about using Ubuntu daily. I was wondering how I could go about expanding the space Ubuntu can use seeing as how I don't have it set up as a separate partition. I'm sorry if this is a really dumb question. haha

---

### Post by WienerWuerstel on 2010-11-26
What do you mean by they are on the same Partition?

Have you used Wubi to install Ubuntu?

---

### Post by emoguitarist06 on 2010-11-26
If they're in the same partition than you must've used WUBI to install Ubuntu inside Windows right?

If so unfortunately you cannot expand Ubuntu
but you CAN backup everything and than remove Ubuntu from Windows and than install Ubuntu side by side with Windows on a separate partition of course

---

### Post by bcbc on 2010-11-26
[How to resize the virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371")

I found that the resize works on newer installs. On some of my older test installs that were banged up it wasn't 100%. But the resize won't touch the current virtual disk, it just creates a new larger copy, so it's safe to try.

Wubi installs are great to try out Ubuntu, but at some point it's a good idea to consider migrating to a partition. So here is a [Howto migrate a wubi install]("http://ubuntuforums.org/showthread.php?t=1519354") in case you're interested.

PS there is a grub update that is breaking wubi installs. Avoid any updates to packages grub-pc and grub-common.

---

### Post by flipper T on 2010-11-26
you could also save space consuming files like music / video to the "windows part" of your disk, freeing up some extra space for ubuntu apps

---

### Post by RiThePirate on 2010-11-27
I chose the "install along side another OS option while installing Ubuntu. Upon further inspection I found that they are in fact on 2 separate partitions but Windows only recognizes the one under  "Computer". However if I go into Disk Management I can resize the Ubuntu partition with no problem. Damn Windows... haha. Thank you all for the quick replies, I guess it just took a little digging to find what I needed.

---

