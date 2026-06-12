---
title: "Grub2 screen resolution too big"
date: 2009-10-19
forum: General Help
---

### Post by nmgarnett on 2009-10-19
Hi
My grub 2 screen resolution is at about 1200x1900 on my 1200x800 laptop and I don't know how to change it. It pops back to the right resolution a couple of seconds after I've logged in. I think I'm running 9.10.
Any help appreciated bearing in mind I am a new convert
Nick Garnett

---

### Post by Giblet5 on 2009-10-19
You can't log in to a grub screen.

Boot sequence for ubuntu:

Push button: observe lights and beeps.
Grub menu: select OS version to run, or wait for default.
Kernel usplash: something to look at besides cryptic PCI init messages.
Desktop login: where you log in.

Which of those is at the wrong resolution?

---

### Post by nmgarnett on 2009-10-19
Kernel usplash
Desktop login

---

### Post by Giblet5 on 2009-10-19
The usplash problem is due to incorrect configuration of grub2. You *should* be able to change it in /etc/grub.d/00_header where GRUB_GFXMODE is defined.

This should set an explicit kernel option (when you do update-grub) that sets the VESA screen resolution as the kernel is starting. If it's a resolution your monitor doesn't support, then what you're seeing is the result of that.

I've never gotten changes to work.

Beta code.....

I would expect the DM (login screen) to use the correct resolution though; the driver is loaded and it can 'see' what your possible resolutions are.

What graphics chip do you have? Did you install a hardware driver for it?

---

### Post by nmgarnett on 2009-10-19
It's just integrated graphics and I didn't install any drivers

---

### Post by Giblet5 on 2009-10-19
> **nmgarnett said:**
> It's just integrated graphics and I didn't install any drivers

Then you'll have to edit /etc/X11/xorg.conf and provide (at least) a "Screen" section that details your actual screen resolution(s).

Example: ```
...
Section "Screen"
    Identifier     "Default Screen"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1600x1080" "1280x960"
    EndSubSection
EndSection
...
```

Integrated graphics chips aren't very good at determining what your monitor can do, unfortunately. That'll change down the road.

---

