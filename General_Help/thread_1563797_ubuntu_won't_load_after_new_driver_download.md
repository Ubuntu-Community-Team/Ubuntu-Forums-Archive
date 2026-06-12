---
title: "ubuntu won't load after new driver download"
date: 2010-08-29
forum: General Help
---

### Post by cybo on 2010-08-29
i'm using lucid lynx. it is a dual boot machine, vista and lucid lynx. i have switchable graphics (at least it is available in windows), intel and ati. ubuntu was working fine but then a pop up showed up asking if i want to install ati drivers. the pop up "said" that drivers were proprietary yet tested on linux systems. i decided to install them. i was asked to reboot after installation which i did. now every time i select ubuntu in the grub the system loads but then it suddenly stops and i get a blank screen. does anybody know what can i do to get my linux back?

any help is appreciated.

---

### Post by arrange on 2010-08-29
If you think the new packages are to blame, you can try removing them.

In the Grub menu choose *recovery mode*, then *netroot* or *root*. Look at the */var/log/apt/term.log* file to see which packages were installed. Then remove them.```
# see the log
less /var/log/apt/term.log
# remove packages
apt-get remove package_name
```

---

### Post by jxtreme on 2010-08-29
At grub select "Ubuntu (recovery mode). Then select failsafe x. The screen will be really small, but usable. If it says that x couldn't load or something  press ok and say that you'll troubleshoot it. Open a terminal and run
```
aticonfig --initial
```. Then reboot.

---

### Post by cybo on 2010-08-30
thanks everyone for the help. i simply reinstalled ubuntu. i know it is very lame approach but i really couldn't wait, i really needed to use linux.

---

