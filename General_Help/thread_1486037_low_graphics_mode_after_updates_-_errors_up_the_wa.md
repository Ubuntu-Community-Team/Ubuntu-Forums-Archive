---
title: "low graphics mode after updates - errors up the wazoo but everything looks fine"
date: 2010-05-17
forum: General Help
---

### Post by dgw on 2010-05-17
My ubuntu install has been screwed up since I upgraded to 10.04. After the upgrade I couldn't boot and had to reinstall grub. Everything was mostly fine after that except an error right when I turn on the computer (but it boots fine after that), and a flickering with the monitor. The flickering only happens when I have just the laptop screen, and I usually use a second monitor along with the laptop screen, so I've been kinda scared to try to fix that issue because I'd rather have an occasional, not-very-annoying flicker than break it entirely. Oh, and a few days or so after the upgrade to 10.04, I ran updates and was again unable to boot, reinstalled grub again.

Today it occurred to me that I hadn't installed updates in a while. I don't know what's up with that. So I installed a whole bunch of updates. I shut down the computer a bit later and took it out. I just turned it on and... I'm in low graphics mode. All the errors when I started the computer made it seem like things were going to be horrible, but the screen actually looks totally normal and there's no flicker. :P I'm sure I'm going to break it entirely if I try to fix this without help. 

The reason for why I'm in low graphics mode:
```
[drm] failed to set drm interface version.
Failed to become DRM master.
failed to get resources: Bad file descriptor.
Kernel modesetting setup failed
Screen(s) found, but none have a usable configuration.
```I need to go home and see if it'll work with my other monitor and back everything up. Any idea what I need to do to salvage this, or should I be thinking about doing a clean install?

---

### Post by BoneKracker on 2010-05-17
Errors up the wazoo...
```
apt-get dist-upgrade 2>/dev/wazoo
```

---

### Post by dgw on 2010-05-17
> **BoneKracker said:**
> ```
apt-get dist-upgrade 2>/dev/wazoo
```
:lol:

Ok, so I went home and turned on the computer and aside from the usual error that I see right when I turn it on, everything seems to be normal, and it's working fine with one display or 2. I didn't do anything to fix it. So, it would seem that my display now works better than it did this morning, despite seeing lots of scary error messages about it. This makes no sense, but whatever, I'm happy it works.

---

