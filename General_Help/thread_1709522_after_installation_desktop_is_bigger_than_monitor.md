---
title: "after installation desktop is bigger than monitor"
date: 2011-03-18
forum: General Help
---

### Post by rgavrilov on 2011-03-18
Ubuntu 10.04-32 bits
I just installed it, and desktop is bigger then the monitor, so I can't get to the menu to change the resolution.
I don't know what desktop it's running.

What do I do now?

This is my first linux system, don't assume anything.

---

### Post by seawolf167 on 2011-03-18
Open a terminal (Applications -> Accessories -> Terminal), or the keyboard shortcut by default is [CTRL][ALT]T, and reconfigure xorg, you'll have a prompt while reconfiguring to select your resolution, use the arrow keys to move up/down, and space to select the one you want.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work, let us know and you can manually edit the config file to change your resolution.

---

### Post by rgavrilov on 2011-03-18
> **seawolf167 said:**
> Open a terminal (Applications -> Accessories -> Terminal), or the keyboard shortcut by default is [CTRL][ALT]T, and reconfigure xorg, you'll have a prompt while reconfiguring to select your resolution, use the arrow keys to move up/down, and space to select the one you want.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```If that doesn't work, let us know and you can manually edit the config file to change your resolution.

I run the command and nothing happens, it just returns to the prompt. What file do I need to change?

---

### Post by rgavrilov on 2011-03-18
```
xrandr -s 1280x1024
```

did the trick. Thank you.

---

### Post by seawolf167 on 2011-03-18
Glad it worked - now that you are up and running, you should check to see if there are any drivers available for your system (specifically your video card).

Go to System -> Administration -> Hardware Drivers, and see if you have any to install

---

