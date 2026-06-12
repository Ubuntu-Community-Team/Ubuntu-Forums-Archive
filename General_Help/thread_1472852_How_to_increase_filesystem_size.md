---
title: "How to increase filesystem size?"
date: 2010-05-04
forum: General Help
---

### Post by HMARS on 2010-05-04
I installed ubuntu on my dual-boot machine from inside windows onto the ntfs partition. What'd I'd like to know is how I go about increasing the amount of space that the Ubuntu filesystem  is allowed to use - right now it only has about 14GB free.

---

### Post by MooPi on 2010-05-04
This looks promising.
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?")

---

### Post by unntrlaffinity on 2010-05-04
Hmars, do you mean that you've used Wubi to install Ubuntu within Windows?

Unfortunately, there's no easy way.  You can use LVPM to move your Wubi install to a dedicated partition, but that requires you to create a dedicated partition for your Ubuntu install.  Do you know how to partition your hard drive?

In other words, you'd be partitioning your hard drive into space for Windows, and space for Linux.  Then copying the Wubi install onto the Linux partition.

[http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

14 gigabytes should be plenty of space for system files, so what you might consider is simply changing your default directories ("bookmarks" within Nautilus, the file manager) where the majority of your user and Home folder data is stored to point to folders on your Windows drive.  The upside of doing this is that files you create will be available easily no matter what OS you boot into.

In other words, point "Documents" to the equivalent directory on Windows, probably something like "/host/Users/Yourusername/Documents", "Videos" to "/host/Users/Yourusername/Videos", "Music" to "/host/Users/Yourusername/Music", and so on.

---

