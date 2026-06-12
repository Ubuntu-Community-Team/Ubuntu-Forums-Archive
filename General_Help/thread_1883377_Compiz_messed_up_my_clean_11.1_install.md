---
title: "Compiz messed up my clean 11.1 install"
date: 2011-11-19
forum: General Help
---

### Post by impelus on 2011-11-19
I was trying to figure out how to change the size of the new launcher in 11.1 and the help said to install compiz. I did that, and when I went in there and played with a few settings, problems started to happen.

I would uncheck a box like animations, the gui would reload, then I checked the box back. If I happened to do the same action twice, it completely killed everything. All that was left was the desktop. Not knowing what to do, I powered the system off. I repeated that process once again and next time I restarted, I only had the desktop environment - no launcher, no other top right settings, etc.

1. How do I fix what compiz did. How do I uninstall when I can't do anything but the desktop.

2. How do I change the launcher. I would like the icons to be a little smaller and possible change it's location.

Thanks for the help in advance.

---

### Post by BillyBoa on 2011-11-19
> 1. How do I fix what compiz did. How do I uninstall when I can't do anything but the desktop.

2. How do I change the launcher. I would like the icons to be a little smaller and possible change it's location.

1. Do a Compiz reset


CTRL+ALT+T open a terminal and write

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

2. Install from Ubuntu Software Center the Compiz Config application. Then run it through dash and go down to Unity plugin. Push it and from the Experimental tab choose the Launcher icon size you want.

---

### Post by impelus on 2011-11-19
I tried that, but after I entered the code, I got a bunch of [ERROR] something about the color. About 8 of them, and then something about compiz core.

I was going to copy and paste it into the reply, but after I did ctrl+c the terminal windows freaked out and moved around and ended up freezing the desktop. Booted back into windows now.

---

Attempted the same thing a second time and got the same result. As soon as I tried to do edit>select all, screen freaked out and shoved the terminal up in the top left and froze. I managed to get a photo with my phone. Not sure if it is any more help.

[IMG]https://lh4.googleusercontent.com/-ni3knGUDZ54/TsdvA-G-RVI/AAAAAAAAAfE/EgA0wzv0ZYM/s720/IMG062.jpg[/IMG]

---

### Post by BillyBoa on 2011-11-19
In such a case try to reinstall Unity

```
sudo apt-get install --reinstall ubuntu-desktop 
```

after that look if the Unity plugin is checked in CompizComfig

---

### Post by impelus on 2011-11-19
That didn't exactly work, but I ran ccsm from terminal and was able to check the unity box and make the icons smaller.

Thanks!

---

