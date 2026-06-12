---
title: "Logout leads to black screen"
date: 2011-11-25
forum: General Help
---

### Post by InfinitySquared on 2011-11-25
Greetings,
I just recently switched over to Ubuntu from Windows and it's great so far. However there's one problem that's bugging me. Whenever I try to logout, I get a black screen and I have to reboot my computer.
I'm running Ubuntu 11.10
I really hope someone helps me out.

Thanks in advance,
InfinitySquared

---

### Post by InfinitySquared on 2011-11-25
bump
help please

---

### Post by raja.genupula on 2011-11-25
[http://ubuntuforums.org/showthread.php?t=1665405](http://ubuntuforums.org/showthread.php?t=1665405)

---

### Post by InfinitySquared on 2011-11-26
It doesn't work cuz im using gnome not kde

---

### Post by InfinitySquared on 2011-11-26
Help please
I'm using lightDM as my default desktop manager and whenever I try to logout the screen turns black , just like it does when you use "sudo stop lightdm" in the terminal
I tried switching to GDM and KDM but the problem still persists.

---

### Post by raja.genupula on 2011-11-26
[http://askubuntu.com/questions/19603/log-out-in-kubuntu-puts-me-to-a-black-srceen](http://askubuntu.com/questions/19603/log-out-in-kubuntu-puts-me-to-a-black-srceen)

actually you're problem was a bug , but we have solution man . 
look at the above link man.

---

### Post by InfinitySquared on 2011-11-27
Yes but that's a solution for Kubuntu with the KDM display manager
I installed KDM and did what the link said but the problem is still there

---

### Post by InfinitySquared on 2011-11-27
I uninstalled LightDM, and now Ubuntu doesn't start at all, even tho KDM is my default display manager

---

### Post by raja.genupula on 2011-11-27
do the final one man 
its have everything 

```
sudo apt-get install --resinstall kubuntu-desktop
```

---

