---
title: "Is mounting a partition on a partition unstable?"
date: 2011-01-19
forum: General Help
---

### Post by David1000 on 2011-01-19
I have come across the following statement:

*"  When a FAT32 partition is mounted at '/media/windows', all access to '/media/windows' and everything below it is transparently handled by the Linux kernel using the 'vfat' module. Applications need not know they're dealing with anything else. However, mounting a partition at a location inside of another mounted partition is unpredictable, unstable, and generally a bad idea. "*

Is it correct?

Most of my partitions are mounted on /home, which is on a separate  partition; and I have one "level 3" partition.  I have been using Ubuntu for nearly three years so far with no problems (except for /home losing it's format once).

David

---

### Post by srs5694 on 2011-01-20
It would be helpful if you'd provide a reference for this quote. As it is, we don't know if it's some random person on a Web forum, a Linux filesystem developer, or something in-between. I've never heard of such "unstable" issues before, and I've been doing nested mounting for years, on and off. (I change configurations with every re-installation, of course.) If there's some authority behind the claim, though, it could be it's worth following that advice; but I'm skeptical of it, based on my own experience.

That said, I can imagine problems that could crop up. Suppose you've got /home on its own partition, and /home/shared on another partition. Now suppose that /home develops a problem that prevents it from mounting. Assuming you don't have a /home/shared directory on root (/), /home/shared will then be unable to mount. If there is such a directory, enabling /home/shared to mount, and if you then mount /home after fixing it, that will hide the contents of /home/shared. In other words, successful use of nested mounts depends on mounting them in the correct order.

Note that I said I could *imagine* problems. I've never before run into this problem, despite years of nesting partition mounts like this. I had to run some quick experiments to confirm what would happen!

---

### Post by David1000 on 2011-01-20
Thanks for your reply.  That is what I thought.

The address of the quote is:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)


David

---

### Post by David1000 on 2011-01-20
I should have added that the quote is the third to bottom paragraph on the page.

David

---

### Post by srs5694 on 2011-01-21
Thanks for the reference. It's a wiki, and without digging through the change log and contacting the individual who entered that information, it's hard to judge the ultimate source of the advice. Without reasoning or references, it's hard to judge its merits.

I'll point out one other thing, though: The root (/) filesystem is itself a "mounted partition" (or at least a mounted filesystem -- it could be on a logical volume inside an LVM, on a CD-ROM, etc.), so whenever you create separate partitions for /home or other filesystems, you're violating the advice on that page. This interpretation may be a bit picky, but since there's no reasoning presented for why it's "generally a bad idea," it's hard to see why mounting /home (or whatever) on root (/) is any different from mounting /home/shared (or whatever) on /home. Both use the same tools and procedures.

Maybe there is some reason not to nest filesystems more than one deep, but if so I don't know what it is.

---

