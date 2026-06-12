---
title: "Ubuntu running inside windows?"
date: 2011-06-19
forum: General Help
---

### Post by bburki on 2011-06-19
Hello,
A couple of months ago I installed Ubuntu 11.04 on my Windows machine using the WUBI installer. Everything works fine, but I noticed that in Windows control panel add/remove programs Ubuntu is one of the programs on the list like any other Windows application. Does that mean that Ubuntu is running inside Windows when I start it up?
Thanks!

---

### Post by prodigy_ on 2011-06-19
> **bburki said:**
> Hello,
Does that mean that Ubuntu is running inside Windows when I start it up?
No. Wubi isn't a virtual machine. It's [a special Ubuntu installer](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29) that can run on Windows and allows you to install Ubuntu from Windows on NTFS (native Windows filesystem) partitions which isn't normally possible.

But yes, you can remove a Wubi-made Ubuntu installation from Control Panel like if it were just a Windows app.

Please note that while the installation process is slightly more user-friendly than creating an actual dual-boot environment with a regular installer, the resulting installation is also more complicated and might be harder to troubleshoot sometimes.

---

### Post by Rubi1200 on 2011-06-19
Hi and welcome to the forums bburki :)

Just to add to what prodigy_ already said, Wubi uses a virtual file-system on the host (in this case Windows), but when you boot into Ubuntu you are, to all extents and purposes, using Linux (with its own file-system etc.).

For more details, see here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

