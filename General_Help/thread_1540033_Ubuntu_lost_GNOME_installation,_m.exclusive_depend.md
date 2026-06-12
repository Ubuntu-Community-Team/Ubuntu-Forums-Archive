---
title: "Ubuntu lost GNOME installation, m.exclusive dependencies when reinstalling GNOME"
date: 2010-07-27
forum: General Help
---

### Post by AndrejaKo on 2010-07-27
I was experimenting with nVidia's proprietary drivers from 256 series. I installed the driver from nVidia's site after uninstalling the driver which  shipped with Ubuntu. After some time (long uptime for system) I noticed that after every reboot nvidia kernel module woudln't be recognised and that I have to recompile it every time. For some time it worked as a workaround, but after 4 or 5 recompiles, the workaround stopped helping. At this time I decided to return to stable drivers. I uninstalled new drivers and installed nvidia-current package. After reboot low-graphics mode would greet me. At that time vesa driver stopped working too. After selecting my username from GDM's prompt, I would get white square  on black background and get back to log-in prompt. After this I tried to solve the problem by purging drivers, xorg gdm and reinstalling them. It didn't help. I installed KDM later KDE and was able to use KDM to get a Konsole window. For some strange reason at the time I could have only one window open. Windows didn't have minimize/restore/close buttons. I decided that I would have to reinstall Ubuntu and gave up on saving it. Few weeks passed. Few days ago I decided to try one more time to save the installation. After apt-get update && apt-get upgrade I installed nVidia 256 drivers from ubuntu-x-swat ppa repository and managed to normally start KDE. 

After this not so short background, here is my problem:

On GDM's session list GNOME isn't listed and I have how KDE4 looks. Among available packages in Synaptic, there is GNOME package. I hope that after installing it, I would be able to go back to GNOME. Unfortunately,it installs epiphany-extensions package which is incompatible with swfdec-mozilla package which is needed as a dependency. 

What should I do to bring GNOME back? I don't feel like reinstalling the system because I already "moved in" and set lots of programs and setting the way I like them.

---

### Post by stlsaint on 2010-07-27
try:
```
 sudo apt-get install gnome-desktop-environment
```

The gnome environment is a meta-package. You must enable the universe repository which im sure you have since you had gnome before.

---

### Post by AndrejaKo on 2010-07-27
I had some problems with -enviroment part. Somehow when I cpoied it to console, a space appeared. 

Everything is fine for now. I'll report after installation.
Everything is working fine for now. Thank you.

---

### Post by stlsaint on 2010-07-27
Please mark the thread as solved using thread tools.

---

### Post by AndrejaKo on 2010-07-27
I marked it just before I edited "Everything is working fine for now. Thank you." in. On my side it says [SOLVED]. A bug in forum software maybe?

---

