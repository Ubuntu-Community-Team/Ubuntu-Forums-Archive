---
title: "Removing WIndows Boot Manager, &amp; use GRUB instead"
date: 2010-06-09
forum: General Help
---

### Post by pinche on 2010-06-09
Hello,

So I just purchased my Asus 1201n with windows 7 pre-installed.  I installed Ubuntu via the windows installer and now at startup I have Windows Boot Manager and GRUB both prompting me to select the OS which I want to boot.

How can I remove Windows Boot Manager and just use GRUB for selecting the OS I want to use?

---

### Post by tommcd on 2010-06-09
> **pinche said:**
> 
  I installed Ubuntu via the windows installer and now at startup I have Windows Boot Manager and GRUB both prompting me to select the OS which I want to boot.
Do you mean that you installed Ubuntu inside Windows using Wubi? 
If that is the case, I would not remove the Windows boot manager since you do not really have Ubuntu installed to a dedicated partition. 
> **pinche said:**
> 
How can I remove Windows Boot Manager and just use GRUB for selecting the OS I want to use?
If you really want to use Ubuntu (and grub) then I would suggest that you do a proper installation of Ubuntu to a dedicated partition on your hard drive. You can set up a dual boot system where you can boot Ubuntu or Windows using grub as the boot manager.
Here are 2 great sites to help you get started:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by philinux on 2010-06-09
> **pinche said:**
> Hello,

So I just purchased my Asus 1201n with windows 7 pre-installed.  I installed Ubuntu via the windows installer and now at startup I have Windows Boot Manager and GRUB both prompting me to select the OS which I want to boot.

How can I remove Windows Boot Manager and just use GRUB for selecting the OS I want to use?

That is perfectly normal for a wubi install. The win bootloader comes up first to let you choose the OS then grub will appear. I would not mess with this.

---

### Post by wilee-nilee on 2010-06-09
Both of these posts are correct. Were you trying to dual boot in the 1st place? wubi seems like a dual boot but technically its not. A real dual boot will give you the best performance and protect Ubuntu by it not being a file in a ntfs partition. If you want to dual boot later on just ask for a little help first if you need to.

---

