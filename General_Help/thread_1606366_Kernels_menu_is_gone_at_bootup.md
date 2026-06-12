---
title: "Kernels menu is gone at bootup?"
date: 2010-10-26
forum: General Help
---

### Post by brallan on 2010-10-26
I am frustrated that I do not see the kernels menu anymore, which had  such useful tools like the different kernels, the ram checker or the  recovery mode kernel, allowing recovery from a botched update, etc. As  of 10.10, I don't even get the kernel messages flashing by, all I get is a  dumbed-down black screen a là windows, then it boots ubuntu without offering me any  of these options. 

How do I get to it, and how do I get it back?

---

### Post by khrosyn on 2010-10-26
Hold SHIFT key when you boot your computer.

---

### Post by NightwishFan on 2010-10-26
Hold shift while booting to see the menu. To make it permanent give the grub a positive timeout in /etc/default/grub. (Make sure you run sudo update-grub).

---

### Post by drs305 on 2010-10-26
If you have a pure Ubuntu installation (no other OS's) you may need to also place a # symbol in front of the following line in /etc/default/grub:
> 
**[COLOR="DarkRed"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10


Open /etc/default/grub for editing as root:
```
gksu gedit /etc/default/grub
```
Make the change, save the file, then run the following to update the menu:
```
sudo update-grub
```

---

