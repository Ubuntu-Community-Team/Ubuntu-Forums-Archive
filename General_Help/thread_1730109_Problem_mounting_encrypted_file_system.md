---
title: "Problem mounting encrypted file system"
date: 2011-04-15
forum: General Help
---

### Post by Techloid on 2011-04-15
Hey, I'm fairly new to ubuntu and I've been having some issues recently. 

I had for a while an ubuntu installation on my external drive because the hard drive on my netbook got corrupted. The problem occurred when the grub was unable to boot into the Ubuntu installation, after that I tried to use a livecd to get at my information. the home folder is encrypted and when I click 'Access-Your-Private-Data.desktop' a command promt quickly appears and vanishes, and nothing happens. I tried manually mounting .private in ecryptfs but in the directory it gives me, the folder names and file names are all ENCRYPTED+gibberish. When I try a chroot even as root user I keep getting Permission Denied. 

Any Advice?

---

### Post by bodhi.zazen on 2011-04-15
[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

---

### Post by Techloid on 2011-04-15
As I said before, chroot keeps throwing me an error

```
chroot: cannot run command '/bin/bash': Permission denied
```Ran with sudo and as root user.

---

### Post by bodhi.zazen on 2011-04-15
That looks like a grave error and when you add in encryption your data is likely lost.

You can try running fsck on the disk, is if there are any errors you can fix.

---

