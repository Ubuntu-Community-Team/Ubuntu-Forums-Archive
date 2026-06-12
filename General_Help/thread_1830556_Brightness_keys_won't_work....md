---
title: "Brightness keys won't work..."
date: 2011-08-21
forum: General Help
---

### Post by josian_220 on 2011-08-21
Hello I was wondering if anyone is having this same issue as I am, I am currently unable to change my brightness level on my laptop using the keyboard combinations to change the brightness level but I am able to do so with the slider with power manager settings (while using Gnome as DE the brightness applet won't work either).

I already change the grub kernel parameters to "quiet acpi_osi=Linux acpi_brightness=vendor splash" and all the similar combinations that people often suggest and I had no luck (actually those made it impossible to change the brightness even in the power manager settings).

Typing in a terminal...

```
pkexec /usr/sbin/gnome-power-backlight-helper --set-brightness 1
```

makes my brightness to go the lowest level and...

```
pkexec /usr/sbin/gnome-power-backlight-helper --set-brightness 10
```

the highest level.

I was wondering if anyone has had this same issue. I don't know if this helps but while using Fedora this issue does not happens, brightness keys will work perfectly fine.

---

### Post by zero2xiii on 2011-08-22
I have the exact same issue.

Running ubuntu 11.04 and 10.04 and a Gigabyte Q1585N laptop.

Powermanager doesn't even work for me, nor does the commands you are using. Also tried the boot options and all that recommended by the "comunity" also no luck.

Currently I am setting my screen brightness using the Nvidia settings manager. Not very effective, but does remove some of the strain on my eyes due to the bright light  8-)

Cherz

---

### Post by josian_220 on 2011-08-23
I think my issue will be fixed when Ubuntu 11.10 releases.

As I said before brightness works on Fedora right now, but only with fedora 15 which uses gnome 3, I've just booted with my live CD of Fedora 13 (32 bit) and brightness keys do not work (the bug is exactly the same as Ubuntu right now, brightness keys wont work but the slider in the power manager does).

I am testing Ubuntu 11.10 alpha 3 right now and it seems to me that the brightness keys are not working at all (rather that bugged), maybe the gnome power manager hasn't been entirely implemented yet (I don't know if this is the case I'm not an expert on the subject just guessing).

---

