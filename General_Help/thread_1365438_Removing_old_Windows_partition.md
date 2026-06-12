---
title: "Removing old Windows partition"
date: 2009-12-27
forum: General Help
---

### Post by HonzaPokorny on 2009-12-27
About a year ago, I started playing with Ubuntu. I started with Wubi and then installed Ubuntu side-by-side with Vista (2 separate partitions). Then several months later, I decided to get rid of Vista. I wiped the Vista partition and deleted it with gparted - Ubuntu is now using the whole disk. 

Now the problem is that when Ubuntu is booting up it still tries to mount that old disk and throws errors. I boots fine, works fine...

How can I remove the old, now non-existent, windows drive? 

When originally installing Ubuntu, I mounted Windows under /windows. 

I'm running Ubuntu 9.10 64-bit. If you need any more information, I am more than happy to supply it. 

Thanks!

---

### Post by QLee on 2009-12-27
[QUOTE=HonzaPokorny]
Now the problem is that when Ubuntu is booting up it still tries to mount that old disk and throws errors. I boots fine, works fine...

How can I remove the old, now non-existent, windows drive? 
[/QUOTE]
Chances are good that you set your fstab to mount that drive, and if that is the case then you need to erase or comment out that line in your fstab.

If you need help with understanding that, have a look at:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

