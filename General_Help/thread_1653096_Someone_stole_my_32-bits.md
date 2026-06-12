---
title: "Someone stole my 32-bits"
date: 2010-12-26
forum: General Help
---

### Post by 96th on 2010-12-26
Hello. I have a *massive* problem with my new Ubuntu installation. I was trying to install Chrome on my laptop through the packages from Google, so I downloaded the 64-bit deb. I opened it, and Ubuntu Software Centre said that the architecture is wrong. I looked in / to see if lib64 is there, but it isn't. I am pretty sure I downloaded and installed the 64-bit version of Ubuntu, so I looked on my pendrive to check. And it does have 64-bit related folders on it. So, where are my other 32-bits gone?!

Also, my touchpad is laggy on Ubuntu. I had fedora before, and my touchpad was working all right. It seems that the touchpad is going to sleep every time after I leave it for a while. I tried to install some drivers for my AMD Radeon X1200 as I think it might be lags, but what drivers do I need to install?

---

### Post by cascade9 on 2010-12-26
In terminal, enter- 

uname -r 

It should show you the kernel release version, and that should make it clear if its 32bit or 64bit. 

As for the x1200- you cant install the ATI drivers for that card on the newer ubuntu versions. The open source driver is all you can use.

---

### Post by 96th on 2010-12-26
2.6.35-24-generic: so, it's not 64-bits? Ugh.

What are the open source drivers called and how can I install them?

//Edit: Is this it: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) ?

//Edit2: I wanted to enable KMS, like it said in this guide: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) ,but when I do update-grub, it says: "/etc/default/grub: 9: radeon.modeset=1: not found". How do I enable it?

---

### Post by dcstar on 2010-12-28
> **96th said:**
> 2.6.35-24-generic: so, it's not 64-bits? Ugh.

What are the open source drivers called and how can I install them?
........

They are already installed and used by default.

---

### Post by mc4man on 2010-12-29
> 2.6.35-24-generic: so, it's not 64-bits? Ugh.
You might rather try any of these instead of uname -r
uname -m
uname -a
arch

---

