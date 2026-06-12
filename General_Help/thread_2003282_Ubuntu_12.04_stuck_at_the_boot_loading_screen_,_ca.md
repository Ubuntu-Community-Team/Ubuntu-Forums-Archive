---
title: "Ubuntu 12.04 stuck at the boot loading screen , can't reach login screen."
date: 2012-06-13
forum: General Help
---

### Post by maizuddin35 on 2012-06-13
Hi everyone !

I think , I need your help .Well I need your help

1. I can't reach my login screen , its stuck at the loading boot screen where the Ubuntu logo is .
2. This problem occur when I remove gdm , and try to reinstall back lightdm.
3. Now I can't do anything much, because I just don't know how. 

4. My idea is...chroot into the system using a live cd, and install back either gdm or lightdm. The thing is I don't know how, because I tried and I failed. (any links?)

anyone can help me with an easier way ?

thank you in advanced. ;)

p/s I'm at my work place using a laptop, can't reach the computer for now...

---

### Post by BBQdave on 2012-06-14
> **maizuddin35 said:**
> 1. I can't reach my login screen , its stuck at the loading boot screen where the Ubuntu logo is .
2. This problem occur when I remove gdm , and try to reinstall back lightdm.
3. Now I can't do anything much, because I just don't know how. 
4. My idea is...chroot into the system using a live cd, and install back either gdm or lightdm. The thing is I don't know how, because I tried and I failed. (any links?)

The most direct and safe (for your data) is to mount and back up your home directory (your data), then do a fresh install of Ubuntu to restore your system.

If you continue attempts to repair your system, I would still recommend backing up your data :)

---

### Post by zombifier25 on 2012-06-14
Try getting in a tty (press Ctrl+Alt+F1), login and run this command:
```
sudo dpkg-reconfigure lightdm
```

---

### Post by maizuddin35 on 2012-06-14
> **zombifier25 said:**
> Try getting in a tty (press Ctrl+Alt+F1), login and run this command:
```
sudo dpkg-reconfigure lightdm
```
 
Can I get into tty when the splash boot is loading ? i think I may try to do it.

---

### Post by maizuddin35 on 2012-06-21
i can't reconfigure it back, due to the "no network" connection. Im using wireless connection and sometimes tethered with my mobile phone. 

does backing up my data and install it back is the only solution ?

---

