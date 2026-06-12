---
title: "Jaunty Configure 1220 x 800 Screen Resolution"
date: 2009-07-27
forum: General Help
---

### Post by rustyz on 2009-07-27
how would i go about adding 1220 x 800 (16.10)screen resolution to the drop down list on Ubuntu Jaunty?

using an Acer P201W Monitor and NVIDIA Drivers

thanks in advance...

---

### Post by rustyz on 2009-07-28
no one knows how to do this?

---

### Post by komputes on 2009-07-30
Highest common resolution between what the monitor is capable of and what the card is capable of, should be a choice in System > Preferences > Display (or in the nvidia setting manager). If not it is most likely a bug. 

Your monitor is capable of a resolution up to 1680 x 1050.

For the model number of your nvidia card please run the command

```
$ lspci -nn

```

Testing:
By deactivating the binary nvidia driver in System > Administration > Hardware Drivers are you able to reboot and set your monitor to 1220 x 800?

I suggest you read the following documentation:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

You may also want to try placing this as the "Screen" section in your /etc/X11/xorg.conf - just make sure that the identifier, monitor and device names match what you currently have in you xorg.conf.

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
    SubSection "Display"
        Modes "1280x1024" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by MikeSD on 2009-07-30
After installing NVIDIA drivers, don't you have "NVIDIA X Server Settings" app in the menu?  Should be possible to generate xorg.conf file with needed settings from there, at least I did so.

---

### Post by rustyz on 2009-07-30
thanks you two...

mike> Should be possible to generate xorg.conf file with needed settings from there

yes mike, it's there...

"just what are the needed settings, and how do i go about that?"

i was able to change the screen res. on Gutsy from terminal with not much of a problem...

Jaunty Jackass is not the same...

if need, i can always change my DPI settings, just the min/max/restore buttons are still too small for my old eyes!

thanks

---

