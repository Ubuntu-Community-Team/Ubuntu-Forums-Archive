---
title: "Permissions Problem"
date: 2012-08-20
forum: General Help
---

### Post by Arif Safwan on 2012-08-20
I'm running 12.04 off a flash drive in order to remove files from a fragged laptop before I reformat and start again with fresh new Ubuntu instead of the Mint I've been running for the last year or so.

Unfortunately, while I can see the folders I want to move, I can't touch them due to Ubuntu thinking that I'm not the owner.

I've tried chown commands, but they fail because the terminal recognises "No such file or directory". They're right there!

How do I find them and change permissions so that I can move them to an HDD?

---

### Post by JazzPotato on 2012-08-20
You'll need to mount the laptop's filesystem:
[http://its.virginia.edu/os/linux/mount.html](http://its.virginia.edu/os/linux/mount.html)

---

### Post by Arif Safwan on 2012-08-20
Yay!

With the laptop HD mounted, I was able to find the proper filepath, and once I'd "chown"ed myself into the position of owner, I was able to use "chmod" to change the permissions and access the files.

Long, but worth it! Hooray for my files and for Jazzpotato

---

