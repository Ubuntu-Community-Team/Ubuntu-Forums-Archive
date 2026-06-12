---
title: "Change TTY Resolution in Karmic Koala"
date: 2009-11-08
forum: General Help
---

### Post by Loosedogz on 2009-11-08
Hi everybody,

I've been searching all day, but it seems that now that Karmic has switched to Grub2, the original Wiki entry ([https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)) no longer applies.

I've been into the new grub configuration (/etc/default/grub) and uncommented the variable "GRUB_GFXMODE" followed by the command "sudo update-grub -u." However, this seems to only apply to the grub bootscreen.

Although it is a rare request, Grub2 has correctly determined the resolution of my monitor to be 1024x768, but I'm looking to lower it to 640x480.

Does anybody have any insight on this?

---

### Post by anandamide on 2009-11-17
I would also be interested in finding this out - to boost my resolution to 1280x1024

---

### Post by d1zzy on 2009-11-19
Chaps:

The settings can be found in /etc/default/grub. Find/replace the following line:

```
GRUB_CMDLINE_LINUX="vga=792"
```

This line will make your TTYs 1024x768x24. Naturally you can use a different code as per the wiki page for different resolutions.

Once you've saved the changes, do a sudo update-grub as per usual.

Cheers

---

### Post by makaveli789 on 2009-11-22
Is it possible to have a widescreen resolution - specifically 1680x1050??

---

### Post by makaveli789 on 2009-11-23
Anyone?

---

### Post by UrbenLegend on 2010-01-04
@makaveli789

I have been trying to look for the same thing. The code is supposed to be vga=369, but Karmic can't support that resolution for some reason (It worked in previous versions though). I've been trying to look for a solution with little success.

---

### Post by Razlo on 2011-08-19
It's an old post, but let's help new visitors. As it is explained in the link above, the following property is deprecated in grub2:
```
GRUB_CMDLINE_LINUX="vga=792"
```
Instead, you will need to change another property:
```
GRUB_GFXPAYLOAD_LINUX=1024x768x32
```
The resolution you input here must be supported by your driver. You will know them by the grub command **vbeinfo**. As you may know, grub console is accessed pressing '**c**' in the OS selection menu.

After editing this /etc/default/grub whit the told property, just do **sudo update-grub** and reboot to see the changes.

Hope it helps new visitors :)

---

