---
title: "partitions"
date: 2011-04-09
forum: General Help
---

### Post by aetherian on 2011-04-09
Hello, sorry if this question is entirely... ah... idiotic, but I figured it best to ask before partitioning.
I wish to resize some partitions, as could be predicted, in order to install something on them. however, my question is, which partition is this operating system even installed on. I am running ubuntu 64 bit server with xubuntu-desktop installed, so as to get 64 bit xubuntu, and I am not sure about my partitions now. I could say with text every single partition, what it is, and stuff about it, but I figure best just to have a big annoying image in my post.

[IMG]http://i.imgur.com/zBQJd.png[/IMG]

Well, not TOO annoying. but anyway, my first instinct would be to resize /dev/sda2, but I also wonder what /boot is exactly _for_ and why I can't see all the numbers for the other ones.

Help would be appreciated.

---

### Post by oldfred on 2011-04-09
I know nothing about LVM other than it is logical partitions, so you are not showing your logical partitions.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by srs5694 on 2011-04-10
First, LVM has nothing to do with logical *partitions*, except to the extent that an LVM partition can *be* a logical partition, as it is here. Instead, LVM is a way to manage logical *volumes* -- that's what the name means: Logical Volume Manager. This may sound like I'm nit-picking about terminology, but I'm not; partitions and logical volumes, although they can both serve as placeholders for filesystems, rely on very different data structures and tools for manipulating them. A failure to understand these distinctions will almost certainly lead to trouble, or at least a great deal of confusion.

Aetherian, what do you want to install? If you want to use the new space for Linux (either in Ubuntu or to install another distribution), you're best off working within the LVM framework; leave GParted (or other partitioning tools) out of it entirely. Instead, install and use kvpm or system-config-lvm to manage your logical volumes, or use the text-mode tools (with names starting in pv, vg, and lv, such as lvresize) to do the job.

If you want to use the space for non-Linux purposes, you'll need to first use the LVM tools to shrink the LVM, then shrink /dev/sda5, and possibly shrink /dev/sda2. IIRC, GParted won't touch LVM partitions, though. I don't recall offhand if kvpm or systtem-config-lvm will shrink LVM partitions, although they certainly can shrink the volumes they contain; if not, you'll need to use fdisk to do the job, which can be a little tricky.

---

