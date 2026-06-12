---
title: "dual boot + virtualization?"
date: 2011-07-21
forum: General Help
---

### Post by princeofnam on 2011-07-21
I'd like the ability to dual boot Windows 7 and Ubuntu.  I'd also like the ability to virtualize that same and separate Windows 7 partition while running Ubuntu if I didn't feel like rebooting.  Is this possible?

---

### Post by seawolf167 on 2011-07-21
[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is the Windows / Ubuntu dual boot guide.

As for the other question, I would clone your Windows partition with [Clonezilla]("http://www.clonezilla.org"), then restore the partition to a virtual machine through [Virtual Box ]("https://help.ubuntu.com/community/VirtualBox")in Ubuntu.

---

### Post by princeofnam on 2011-07-21
I'm confused.  It seems from the website's description that clonezilla is designed for OS backup?  Is that applicable to launching the separately partitioned Windows 7 while running Ubuntu?

---

### Post by seawolf167 on 2011-07-21
> **princeofnam said:**
> I'm confused.  It seems from the website's description that clonezilla is designed for OS backup?  Is that applicable to launching the separately partitioned Windows 7 while running Ubuntu?

Launching no, but restoring to a virtual machine from within Virtual Box then running that virtual machine (an identical copy of your Windows partition) from within Ubuntu, yes. [Here ]("http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html")is a little how-to.

---

