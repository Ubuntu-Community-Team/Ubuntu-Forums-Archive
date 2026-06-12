---
title: "Splash Screen Forever"
date: 2012-01-01
forum: General Help
---

### Post by xedth2 on 2012-01-01
Hello,

I just did a brand new install of Ubuntu 11.10.  I uninstalled unity and installed LXDE.  I want the machine to boot to TTY1 so I went into /etc/grub.d and changed the line with vt.handoff=7 in 10_linux into vt.handoff=1 then did sudo update-grub.  But for whatever reason the machine just sits at the splash screen forever.  I can CTRL-ALT-F1 and get into TTY1 just fine.  

I tried using lubuntu but for whatever reason it kept dropping my wifi.  I'm using lubuntu on another machine in the house and it's doing the same thing.  I booted into windows and everything with the wifi works fine.  So now I'm back to Ubuntu.

Thank you for the help.

---

### Post by 2F4U on 2012-01-01
Did it start into the LXDE desktop before the change from tty7 to tty1?

---

### Post by xedth2 on 2012-01-01
> **2F4U said:**
> Did it start into the LXDE desktop before the change from tty7 to tty1?

Nope it litterly just kept looping the splash screen.

---

