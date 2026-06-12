---
title: "wireless driver only works in old kernel --- help /pleeeeeaaase/!!"
date: 2009-11-16
forum: General Help
---

### Post by nerdy_kid on 2009-11-16
I am working on a pc that has no wired internet; only wireless (it was fun getting the wireless drivers installed).  The wireless drivers only work on the 2.26.28-11 kernel, which is the kernel it was running when i installed the drivers.  I am trying to use a webcam with the PC, and found out i need to be running a newer kernel.  However, when i try to run the newest kernel 2.26.28-16 (this is Jaunty btw) the wireless no longer works.  It is recognized via lspci but no farther.  I tryed install installing the wireless drivers again from the newest kernel by extracting the firmware out of the same file i did the last time and putting it in the same place -- /lib/firmware/, to no avail.  the kernel is using the 'ssb' driver which is not the right one.....  ????

sorry to be long winded lol

---

### Post by nerdy_kid on 2009-11-16
anyone?

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
What wireless card you using?

---

### Post by nerdy_kid on 2009-11-17
i think it is 
14e4:4320


its a Broadcom PCI card that is supposed to use the b43 driver -- not b43 legacy

---

### Post by nerdy_kid on 2009-11-17
isnt there a config file somewhere i can edit?

---

### Post by nerdy_kid on 2009-11-18
come on!! this is serious! This is a Windows XP vs Ubuntu war at a friends house -- i /need/ this fixed!

---

### Post by philinux on 2009-11-18
Have a look through a few of these guides.

[Wireless]("http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-GB:official&hs=TV5&ei=CvMDS--oIpTb-Qb_4OGtCA&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=ubuntu+troubleshoot+wireless&spell=1")

---

### Post by nerdy_kid on 2009-11-18
it does work -- in an old kernel.  I cant get the driver to install in the new kernel -- i /think/ that the installed drivers are always supposed to work in every kernel?

---

### Post by philinux on 2009-11-18
> **nerdy_kid said:**
> it does work -- in an old kernel.  I cant get the driver to install in the new kernel -- i /think/ that the installed drivers are always supposed to work in every kernel?

You need to do the diagnostics with the new kernel from some of the links. 

Is your system fully up to date. Maybe connect wired and do an update with the new kernel. Apps>Access>Terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by EJeanmaire on 2009-11-18
> **nerdy_kid said:**
> it does work -- in an old kernel.  I cant get the driver to install in the new kernel -- i /think/ that the installed drivers are always supposed to work in every kernel?

Make sure your driver isn't being blacklisted in one of the blacklist*.conf files in /etc/modprobe.d/

---

