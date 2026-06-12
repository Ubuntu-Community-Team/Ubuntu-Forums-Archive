---
title: "Use different Xorg drivers on boot"
date: 2011-11-11
forum: General Help
---

### Post by pixmin on 2011-11-11
Hi,

I have an optimus card with both an onboard Intel HD3000 and an Nvidia card. I'm not satisfied with the current options offered (including bumblebee and ironhide) so I would like to be able to have to options when I boot, either use/load only the nvidia driver/settings or the intel one.

How can I do that?

(I'm thinking having two options in the grub menu and choose either to boot with an nvidia setup and load the nvidia driver or the intel one)

Thanks.

---

### Post by mtron on 2011-11-11
unfortunately it's not that easy. Optimus support is still a huge mess on Linux.

Some laptops support "exclusive" vga modes for either intel or nvidia, but many laptops don't play the game like this.

so, what's your precise laptop model?
do you have an option to select the vga chip in your bios?
if not, is your laptop equipped with a HDMI port? (if so, chances are pretty good your model supports exclusive vga modes via acpi_calls.)

---

### Post by pixmin on 2011-11-11
> **mtron said:**
> unfortunately it's not that easy. Optimus support is still a huge mess on Linux.

Some laptops support "exclusive" vga modes for either intel or nvidia, but many laptops don't play the game like this.

so, what's your precise laptop model?
do you have an option to select the vga chip in your bios?
if not, is your laptop equipped with a HDMI port? (if so, chances are pretty good your model supports exclusive vga modes via acpi_calls.)

Hi, thanks for the reply. I have a Thinkpad T420. So I can chose to run either nvidia or intel from the BIOS, that's not the problem, the problem is to be able to start ubuntu with the driver/card I decide to start the computer with in the BIOS (basically whether I'm plugged in or on battery)

I can live with having to reboot to set the graphic card I want to use (although I think it should just work, of course) but I'm not sure how to go about setting this up.

Thanks for your help :)

---

### Post by mtron on 2011-11-11
ah, well lucky you ;)

if you can switch via bios, it's not difficult. You need to set the corresponding driver in xorg.conf and use update-alternatives to point xorg to the proper ld.so.conf files.

e.g. for intel (assuming you run the i386 version of ubuntu):
```
update-alternatives --set i386-linux-gnu_gl_conf /usr/lib/i386-linux-gnu/mesa/ld.so.conf
```

and in /etc/X11/xorg.conf adjust the device section to read the line
```
Section "Device"
...
    Driver         "intel"
...
EndSection
```

the settings for nvidia are:
```
update-alternatives --set i386-linux-gnu_gl_conf /usr/lib/nvidia-current/ld.so.conf
```

```
Section "Device"
...
    Driver         "nvidia"
...
EndSection
```

now restart your display manager / Xorg and that's it. I have created myself a startup script that does this automatically before the display manager starts, so it works automatically.

---

### Post by pixmin on 2011-11-11
> **mtron said:**
> ah, well lucky you ;)

if you can switch via bios, it's not difficult. You need to set the corresponding driver in xorg.conf and use update-alternatives to point xorg to the proper ld.so.conf files.

e.g. for intel (assuming you run the i386 version of ubuntu):
```
update-alternatives --set i386-linux-gnu_gl_conf /usr/lib/i386-linux-gnu/mesa/ld.so.conf
```

and in /etc/X11/xorg.conf adjust the device section to read the line
```
Section "Device"
...
    Driver         "intel"
...
EndSection
```

the settings for nvidia are:
```
update-alternatives --set i386-linux-gnu_gl_conf /usr/lib/nvidia-current/ld.so.conf
```

```
Section "Device"
...
    Driver         "nvidia"
...
EndSection
```

now restart your display manager / Xorg and that's it. I have created myself a startup script that does this automatically before the display manager starts, so it works automatically.

Thanks a lot for the reply, but I'm not sure to fully understand. You have two xorg.conf? Or two Section "Device"? I'm going to find how what you mean by use update-alternatives (if it's a kernel/boot option, a command to run on start...)

But thanks for your help so far :) Much appreciated!

---

