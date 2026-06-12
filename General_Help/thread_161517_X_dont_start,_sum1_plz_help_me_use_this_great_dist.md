---
title: "X dont start, sum1 plz help me use this great distro"
date: 2006-04-17
forum: General Help
---

### Post by nic886 on 2006-04-17
I have ubuntu breezy and installation goes fine up until the time for X and the login manager to start comes and the system hangs with a non-blinking CLI cursor at the top of the screen. also, does ubuntu include the kernel headers, GCC, etc needed to compile kernel modules?

any suggestions would b appreciated cos this looks like the best distro from what ive seen. 

](*,)

---

### Post by Hairy_Palms on 2006-04-17
press ctrl+alt+f2 to take you to a terminal, 
then type sudo dpkg-reconfigure xserver-xorg
setup your monitor and then restart your computer

---

### Post by Qrk on 2006-04-17
[QUOTE=nic886]also, does ubuntu include the kernel headers, GCC, etc needed to compile kernel modules?
](*,)[/QUOTE]

Yes and no, you need to install gcc by 

```
sudo apt-get build-essential
```

But you shouldn't need to compile kernel headers, as they are released as .deb files and are intallable through synaptic. Unless you want the absolute latest version of the kernel, which isn't really recommended.

---

