---
title: "Window management is messed up :("
date: 2011-10-16
forum: General Help
---

### Post by searchfgold6789 on 2011-10-16
Hi,
When I updated Kubuntu to Ocelot, (the name of the next release should have been Pernicious Penguin :() My window management became messed up, please see screenshot. It still works, but it's layout is all messed up because it appears to be wanting to handle the windows under a different screen resolution than they actually are, which greatly hinders my productivity, productivity being the main reason why I switched to KDE in the first place.
Anyway, my graphics drivers are all properly installed, and I get the occasional crash, but hey, it's Nvidia.
A funny thing is that, when I run "kwin --replace" in Byobu, kwin says I have the NV30 GPU, but the fact remains that I have the NV34. 
:---) <- kwin
So any help would be appreciated either in fixing the problem or determining what is going on! Thank you so much.
 - search

---

### Post by searchfgold6789 on 2011-10-16
Sorry, I forgot to upload the screenshot. Here it is!

---

### Post by searchfgold6789 on 2011-10-17
SOLVED.
I had to type in:
```
kwin --graphicssystem=native --replace &
```

---

### Post by searchfgold6789 on 2011-10-19
UNSLOVED.
Kwin is now **crashing** for no apparent reason and I have to do a "sudo service kdm restart" out of tty1 whenever it happens, usually after I hover my mouse over a window in the taskbar or Press Ctrl-F8 to present the workspaces.
I have no idea at this point what is going on, and this is after I switched back to 11.04. I would be more than happy to create a KDE bug report or look for an existing one if someone could clarify this for me!
Thanks!
 - search

---

### Post by searchfgold6789 on 2011-10-20
Still an issue after I update KWin.

---

### Post by searchfgold6789 on 2011-10-21
Bump.

---

### Post by linux_nub on 2011-10-23
lol

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **linux_nub said:**
> lol

what a mess..  jeez..  Why do they tell users to upgrade their systems if all it does is ruin what they have??  lol  If it ain't broke, why fix it?:lolflag:

---

### Post by searchfgold6789 on 2011-10-24
> **linux_nub said:**
> lol
:lolflag: 




Actually, at this point it's more because of KWin than anything else. I downgraded to 11.04 again, you see, but since KWin updated I'm still having problems. I'm a headless chicken right now.

---

### Post by dniMretsaM on 2011-10-24
System Settings -> Desktop Effects -> Advanced -> change Compositing type and see what happens.

EDIT: You'll have to log out and then back in again for it to take effect.

---

### Post by searchfgold6789 on 2011-10-24
Thank you for the reply. I changed the compositing type to "XRender" as opposed to OpenGL. It worked for fixing the Taskbar Thumbnails and the Present Windows, but XRender sucks. I lost my desktop cube, etc.

---

### Post by searchfgold6789 on 2011-10-24
Another error: I can't get the desktop sphere or desktop cylinder. :( When I press te designated keyboard shortcuts nothing happens.

---

### Post by searchfgold6789 on 2011-10-27
Bump, maybe I'll post this to the KDE forums as well.

---

### Post by searchfgold6789 on 2011-11-02
OK, I solved the original issue with the taskbar thumbnails and Present Windows effects by setting the scaling method to "Smooth" instead of "Accurate". You can see the official bug [here]("https://bugs.kde.org/show_bug.cgi?id=285131").

Now I'll reboot and see if the desktop cylinder/sphere is fixed.

---

### Post by searchfgold6789 on 2011-11-07
Well, it wasn't. Any suggestions on fixing the desktop cylinder/sphere?

---

