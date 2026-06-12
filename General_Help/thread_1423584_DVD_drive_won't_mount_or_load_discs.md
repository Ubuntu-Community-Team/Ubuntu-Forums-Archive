---
title: "DVD drive won't mount or load discs"
date: 2010-03-06
forum: General Help
---

### Post by Blimpsgo90 on 2010-03-06
unable to mount cdrom0     
mount: special device /dev/scd0 does not exist

I know the drive is hooked up via SATA.

It has worked before, and I have no idea why it isn;t working now. And I have made no BIOS changes since it worked once.  The only change is I installed the newest kernal, that I can think of.

I ran accross someone asking someone with a similar problem to run:

ls /dev | grep cd

so I did and I get:
andrew@andrew-desktop:~$ ls /dev | grep cd
pktcdvd

---

### Post by Blimpsgo90 on 2010-03-06
Oh and I am using Ubuntu 9.10 X64 if that makes any difference.

---

### Post by flippo on 2010-03-06
My CDROM device actually shows up as sr0, all the extra /dev devices are sym-links.  I'm not sure how to figure out what device your cdrom drive is actually associated with though...  If I figure it out, I'll let you know.  You can see the linking on symlinks with "ls -l /dev" though, if that helps you in any way.

---

