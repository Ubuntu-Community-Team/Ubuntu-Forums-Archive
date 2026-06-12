---
title: "Need to make a deb and set up a ppa.  No idea how."
date: 2011-09-24
forum: General Help
---

### Post by ninjaaron on 2011-09-24
So, I made this bitmap font (in plain bdf formate) to use on my computer, and I uploaded it as a tarball in a thread here.  Some people liked it, and requested I host it at github.  While there were quite a few steps to that, the directions were clear enough, and it's hosted there now. It's [here]("https://github.com/ninjaaron/bitocra").  Someone has already made a script to build a package for Arch and posted it in the AUR.  Now people are asking for a PPA.

I looked at the the Ubuntu wiki for creating deb packages.   There weren't exactly instructions.  There was a lot of information, but it was organized in a way that made it difficult for me to figure out what to do.  I was about to install hundreds of MB of developer tools and set up a chroot environment and all this crazy stuff, but I figured there must be an easier way.  In Arch, you can just create a package by writing a short bash script and running it through an auto package building program.

Anyway, is there a simple way to build a simple deb just to unpack a tarball and put it's contents in /usr/share/fonts/misc or whatever?

---

### Post by dino99 on 2011-09-24
some howto:

[http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)

[http://users.telenet.be/mydotcom/howto/linux/package.htm](http://users.telenet.be/mydotcom/howto/linux/package.htm)

---

### Post by ninjaaron on 2011-09-24
This looks promising.  I'll mark the thread as solved for now, and if I run into trouble, I'll "unsolve" it.

---

