---
title: "Grub won't start, I'm not dual booting windows"
date: 2010-01-27
forum: General Help
---

### Post by toldu17butilied on 2010-01-27
Right, so I've looked high and low for the answer to this problem and haven't found it, although I've found a million and a half threads about grub especially when it comes to dual booting windows. Which I'm not. What I am though, I suspect, is an idiot who shouldn't mess around with my computer at 4 am.

So the problem is every time I turn on my pc, grub tells me it can't find a file system and goes into recovery mode. Can't boot into ubuntu at all. Am using the live disk to type this. 

I also think I know why grub is doing this, I was dual booting windows before, I had windows installed originally, added ubuntu to a new partition. Was having problems with grub. Figured that reinstalling it wouldn't be a bad idea, it might fix it. In that process I did something rather stupid, I accidentally installed grub to my other internal hard drive. There is no operating system on it. Just movies, music, etc. The problem, I think, is that my second hard drive is sda, and the one with my os is sdb, which I suspect means that grub is loading from sda and finding no operating system, rather than from sdb. (It's like that because my larger drive wouldn't fit into the sda slot on my computer, long story.)

Which leaves me with a rather simple question that seems impossible to find an answer for. How do I remove grub from sda?

---

### Post by kusumoto on 2010-01-27
Grub should just be the in the mbr in your sda. If you delete that, it should remove grub without any damage to your media files.
Just make sure you have sda mounted while in your live cd and try this from a terminal.

*dd if=/dev/null of=/dev/sda bs=446 count=1*

---

### Post by undecim on 2010-01-27
> **kusumoto said:**
> Grub should just be the in the mbr in your sda. If you delete that, it should remove grub without any damage to your media files.
Just make sure you have sda mounted while in your live cd and try this from a terminal.

*dd if=/dev/null of=/dev/sda bs=446 count=1*

Call me naive, but I don't think that is quite right. /dev/null contains 0 bytes, and so 0 bytes would be overwritten. I think /dev/zero would be correct.```
dd if=/dev/zero of=/dev/sda bs=446 count=1
```You could also change the boot order of hard drives in your bios, if you are comfortable doing that.

[QUOTE=toldu17butilied]What I am though, I suspect, is an idiot who shouldn't mess around with my computer at 4 am.[/QUOTE]
Don't be so hard on yourself. GrUB can be tricky.

---

### Post by Leppie on 2010-01-27
it doesn't matter in which mbr grub is installed, it should link to the boot or ubuntu partition during install.

could you please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

