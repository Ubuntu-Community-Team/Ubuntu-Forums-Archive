---
title: "Missing Space"
date: 2011-12-11
forum: General Help
---

### Post by Nasair on 2011-12-11
I have about a TB of space being "used" but can't find it.
I've looked at:
[http://www.linuxforums.org/forum/ubuntu-linux/136962-missing-space.html](http://www.linuxforums.org/forum/ubuntu-linux/136962-missing-space.html)
[http://www.linuxforums.org/forum/red-hat-fedora-linux/134232-disk-full-but-not.html](http://www.linuxforums.org/forum/red-hat-fedora-linux/134232-disk-full-but-not.html)
[http://ubuntuforums.org/showthread.php?t=623496](http://ubuntuforums.org/showthread.php?t=623496)

And the tools below were mentioned:
[http://en.wikipedia.org/wiki/Lsof](http://en.wikipedia.org/wiki/Lsof)
[http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/](http://www.walkernews.net/2007/02/28/tune2fs-increase-linux-free-disk-space/)

So I've deleted files, empty trash, used disk analyzer (and did a manual properties on folders, and I've tried restarting the computer as well. I can't seem to find the missing space. The only thing weird is that /proc doesn't show it as using space when I look at the properties. 35,251 files are found but it says it totals 128 TB, and obviously my drive isn't this big. My drive is 2 TB by the way on EXT4 with Ubuntu 11.04.

I'm not sure what I'm missing, nor do I know what I should be looking for. Please give me any advice you can. Thank you, Nasair

---

### Post by Nasair on 2011-12-24
Figured it out, simple mistake. I have files that aren't accessable by me because they were put there from another computer with a samba share and given to "nobody" and I deleted them using sudo nautilus...had to manually delete them from the root's trash bin.

:lolflag:

---

### Post by hansdown on 2011-12-25
Glad you fixed it, Nasair.

Good work.

This can be helpful, to other users.

---

