---
title: "I've got to change my loading screen..."
date: 2011-12-15
forum: General Help
---

### Post by enterdavertex on 2011-12-15
I just installed my new desktop environement xfce . But the loading page is kinda like kinky for me though.. i just wanted to re-enable the basic ubuntu loading screen...

Thank you in advance !

---

### Post by N00b-un-2 on 2011-12-16
I'm assuming you're talking about plymouth, the animated boot screen before your desktop boots.  If you installed the xubuntu-desktop package over Ubuntu then it would have been overwritten. to fix it execute the following

```
sudo apt-get install plymouth-theme-ubuntu-logo
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
sudo reboot
```

---

