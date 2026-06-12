---
title: "Lost control of mouse in 11.10/Gnome3/Nvidia"
date: 2012-06-25
forum: General Help
---

### Post by hangfire on 2012-06-25
I have a user that booted up this morning and got a strange looking mouse pointer that flashes across the screen in 3 places when it moves. Can't actuate any Gnome Shell 3 menus in the top 1/3 of the screen. Right click brings up the desktop context menu at most 2/3 of the way up the screen.

We've tried undocking, removing all other USB, touchpad, another mouse, all no difference. User is communicating remotely through Windows dual-boot but needs Ubuntu so this is going to be a tough debug. Thankfully there is a dual boot to a working O/S.

System info: Dell e6520, 11.10, Ubuntu-provided Nvidia drivers, Gnome Shell 3. Everything works under Windows 7.

---

### Post by dino99 on 2012-06-25
i've had same issue but with Quantal testing only, so is this system using some unstable packages from ppa ? In such case purge them (ppa-purge .....)

---

### Post by hangfire on 2012-06-25
> **dino99 said:**
> i've had same issue but with Quantal testing only, so is this system using some unstable packages from ppa ? In such case purge them (ppa-purge .....)

Thanks dino. There was not much in the way of custom PPA's except for touchpad-indicator, which was installed but not active.

We tried switching to nouveau but apparently this laptop chipset (Optimus, turned off sharing in BIOS) is not supported. nv didn't work either. VESA worked. Stepping down from 1920x1200 to 1024x768 is not very practicable, though, but it proved the situation was video driver related.

We ended up using the command line upgrade to 12.04 and then installed the Ubuntu provided Nvidia proprietary drivers, which works. For now.

It's nice to know that Ubuntu is keeping up their grand tradition of pooching our systems once a year. I suspect having the combination of Gnome 3/Nvidia proprietary puts us a little too far off Canonical's testing plan. I may start pushing Mint for Gnome users.

HF

---

### Post by hangfire on 2012-07-02
Now its happening to me under 12.04. Tried everything, booting undocks, all USB removed, etc. May have to move this system to another Distro.

---

