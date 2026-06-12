---
title: "How do I expand my storage space?"
date: 2010-04-28
forum: General Help
---

### Post by teasplurt on 2010-04-28
I created a dual boot on my computer with windows vista and ubuntu using the wubi ubuntu installer for windows, and my ubuntu boot is limited to 15gb of hard drive space.  My hard drive in actuality has about 150gb left on it.  How do I expand the amount of storage ubuntu is allowed to use?

---

### Post by ttshivers on 2010-04-28
This article might help you:  [http://ubuntuforums.org/archive/index.php/t-244233.html](http://ubuntuforums.org/archive/index.php/t-244233.html)

---

### Post by Leppie on 2010-04-28
is the 150gb free space in the windows partition or is it real free space (unallocated, hence no partition)?

---

### Post by gadolinio on 2010-04-28
Mmm I'm not sure, but as far as I know when you install ubuntu using wubi you have a fixed amount of disk space. It's not a partition you can resize. And even when you install it in the first place, Wubi lets you destinate up to 30 GiB to ubuntu. So I think that even if you manage to increase those 15GiB, you'll find a maximum of 30GiB in the end.
Hope I'm wrong!

---

### Post by oldfred on 2010-04-28
Wubi is more of an extended test like the liveCD but allows updates and ease of use for windows users as it is inside the windows partition, uses the windows boot loader and is uninstalled like any windows program.

If you find you like Ubuntu and now want more space it may be time to do a full install with dual boot in separate partitions.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

I have not seen anything yet for Lucid but then it is not out till sometime Thursday. Older instructions are basically the same. the main difference with Ubuntu is grub has now been replaced with grub2 and has totally different instructions on reinstalling and updating.
APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

---

### Post by gadolinio on 2010-04-29
> **oldfred said:**
> Wubi is more of an extended test like the liveCD but allows updates and ease of use for windows users as it is inside the windows partition, uses the windows boot loader and is uninstalled like any windows program.

If you find you like Ubuntu and now want more space it may be time to do a full install with dual boot in separate partitions.


+1.
I used LiveCD for a week, then wubi for a couple of months, and then did a full install.

---

### Post by gordintoronto on 2010-04-29
If you open "computer" in Nautilus, it should show you all your partitions. You can save data in the Windows partition(s) and access everything from there.

---

