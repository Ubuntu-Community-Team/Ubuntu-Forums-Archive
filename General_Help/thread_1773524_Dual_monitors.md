---
title: "Dual monitors"
date: 2011-06-02
forum: General Help
---

### Post by Musket on 2011-06-02
Hi, [I]I am new to Linux and have come from the windows environment. Forgive me if I use windows terminology.

I have installed Ubuntu 11.04 on a separate hard drive and the installation went well. I am using it now to make this post.

When I first tried Ubuntu out using the CD I created from the iso file, I was able to view both my monitors. Now that I have installed Ubunto to a spare hard drive I can only view my primary monitor. I have gone into system settings and monitor preferences and it is unable to detect my second monitor.

My graphics card is an Nvidia GTX275 and my second monitor runs off the HDMI socket, don't know if that makes a difference. Is this a driver issue?

Any help would be appreciated.

Tony
[/I]

---

### Post by Grenage on 2011-06-02
Hi there,

Under *Additional Drivers*, have you tried enabling the recommended driver?  Assuming you have, do you have nvidia-settings installed?  It's a GUI control for nvidia displays:

```
sudo apt-get install nvidia-settings
```

---

### Post by Musket on 2011-06-02
Sorry, I don't understand the code bit. I assume it is to be typed directly into a command line somewhere. Does it install the nvidia drivers.

Sorry for my ineptitude, I am comfortable with windows but Linux is a foreign language.

Tony

edit, under additional drivers, it shows no proprietary drivers are in use on this system, but it also shows NVIDIA accelerated graphics driver. Licence proprietary

---

### Post by iclestu on 2011-06-02
> **Musket said:**
> Sorry, I don't understand the code bit. I assume it is to be typed directly into a command line somewhere. Does it install the nvidia drivers.

Sorry for my ineptitude, I am comfortable with windows but Linux is a foreign language.

Tony

do ctrl+alt+t to give you a command prompt in gnome

yeah - the command installs the package 'nvidia-settings'

---

### Post by Grenage on 2011-06-02
> **Musket said:**
> Sorry, I don't understand the code bit. I assume it is to be typed directly into a command line somewhere. Does it install the nvidia drivers.

Sorry for my ineptitude, I am comfortable with windows but Linux is a foreign language.

Tony

No problem, it was my fault for assuming.  The command does not install the drivers, merely the graphical interface for changing settings.  You'll still want to install the drivers by enabling them in A*dditional Drivers*; if you're using the default 11.04 interface, just select the top left button and type "Additional Drivers" in.

The installation of *nvidia-settings* can be done via a command line (Ctrl-Alt-T), or via the *Synaptic Package Manager*.  To do it via the command line, just enter the previous command, and enter your password when requested.  To do it via the Package Manager, just type Synaptic into the same search box, then do a search for "nvidia-settings".

---

### Post by iclestu on 2011-06-02
> **iclestu said:**
> do ctrl+alt+t to give you a command prompt in gnome

yeah - the command installs the package 'nvidia-settings'

oooo - if you prefer, you could no doubt find it in the gui, ubuntu software centre but the command is probably easier especially with a cut and paste :)

---

### Post by Musket on 2011-06-02
I'm back in windows. Don't know what I did but I got 2 monitors displaying unfortunately, the main desktop is on the second monitor and the mouse will only move around the main monitor where there is nothing to click on.

My head is hurting so I will go and tidy up the garage and come back later. If all else fails I can always reinstall and start again.

Tony

---

### Post by Musket on 2011-06-02
Fixed it, Thanks for your help. On to the next issue
Tony

---

