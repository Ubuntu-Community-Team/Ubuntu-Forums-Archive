---
title: "Change Xubuntu GDM/usplash theme back to Ubuntu defaults in 9.10"
date: 2009-11-02
forum: General Help
---

### Post by ninjabob7 on 2009-11-02
I didn't realize I was running Xubuntu until I upgraded - I started with a vanilla Ubuntu, then installed the Ubuntu Studio package, then installed XFCE (I thought from the xfce4 package, but apparently from the xubuntu-desktop package). Anyway, the first splash image I see (after the bootloader) is a plain white Ubuntu logo with no progress bar. I tried to change it, but none of the old splash images are there - is there some way to reinstall them?
The next thing I see is the hideous Xubuntu splash with the tree and sparkles, then it goes to a login screen which seems to be a horrible combination of XFCE and GNOME parts. I can't find any way to change this - I managed to change the background for the actual login screen by following some other thread but the Xubuntu splash still shows up before and after.

---

### Post by jrrader on 2009-11-03
It's just that when you download another desktop the splash from the new desktop gets set as the default.  Download "startup-manager."  Open it (system -> administration -> StartUp-Manager).  Click on the appearance tab and select the boot spash you want to use.

---

### Post by cariboo on 2009-11-03
Unfortunately startupmanager no longer works for karmic. 

Have you tried installing gdm?

```
sudo apt-get install gdm
```

---

