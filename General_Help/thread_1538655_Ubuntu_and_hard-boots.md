---
title: "Ubuntu and hard-boots"
date: 2010-07-25
forum: General Help
---

### Post by TheAlien on 2010-07-25
Hi!

I've been struggling with a program that made Ubuntu completely freeze, so I had to hard-boot by using the reset button on my computer. It was my mistake that the program hanged, and it works now. But during the testing, I had to do hard-boot for like 10 times or so. But my system always booted fine and nothing seems to be affected by it.

I heard a long time ago that this is a no-no on Linux and Unix. What do you think?

I'm using the ext4 file system btw.

---

### Post by collinp on 2010-07-25
It's never a good idea to hard reboot your system, but there are several mechanisms in place to help prevent or mitigate damage to the filesystem in such a case.

ext4 is a "Journaling File System", which means that it keeps track of the changes it's about to do in a form of journal. This helps to minimize data loss in case of a hard reboot or shutdown. If you're interested, more information can be found here: [http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

---

