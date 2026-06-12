---
title: "Blank screen with GRUB2, Plymouth and Console Mode"
date: 2011-10-18
forum: General Help
---

### Post by sarton85 on 2011-10-18
Since I upgraded from Ubuntu 11.04 to Ubuntu 11.10 I have a blank screen (no screen input) when booting my computer, from the BIOS screen to the moment that the xserver starts and LightDM comes up. This means that I cannot see both GRUB and Plymouth. I can still select Ubuntu 11.10 or Windows 7 using the arrow keys, which shows that GRUB is working, but not visible.

I also get a blank screen when I switch to Console Mode (CTRL+ALT+F1 - F6). 

I tried this with Ubuntu 11.10 32bit and 64bit and both are giving me the exact same results. I use an Nvidia Graphics Card and I am running the current Nvidia driver. Uninstalling the Nvidia driver doesn't change the problem. It is very annoying not being able to see GRUB or use Console Mode.

What can I do to figure this problem out?

---

### Post by sarton85 on 2011-11-14
Because of the blank screen problem and (a lot) of other bugs in 11.10 I did a clean install of 11.04.

Right now I have the same problem as described in my first post again, but now in 11.04.

Could this be a problem with the latest Nvidia driver? I have nvidia-current installed. The problem is, the screen was also blank before I installed the restricted driver, during my first reboot after install.

---

### Post by WasMeHere on 2011-11-14
Hi sarton85,

I think you should try some boot-options according to the following post
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11451221&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11451221&postcount=4")

Look for (in the links)
> Changing boot options Temporarily for an Existing Installation
See the Grub2 page.

Changing boot options Permanently for an Existing Installation
This can be done by :
    *       manually editing GRUB2 configuration file then updating GRUB
    *      or using the "GRUB options" tab of Boot-Repair then Apply. 

Have fun finding out :-)
Olle

---

### Post by sarton85 on 2011-11-14
> **Olle Wiklund said:**
> Hi sarton85,

I think you should try some boot-options according to the following post
[[COLOR=RoyalBlue]_http://ubuntuforums.org/showpost.php?p=11451221&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11451221&postcount=4")

Look for (in the links)


Have fun finding out :-)
Olle

Thanks, I see there are probably some useful tips in this thread. I'm going to try them out.

---

### Post by sarton85 on 2011-11-14
@Olle Wiklund

Thanks! This solved my problem. Grub, Plymouth and Console Mode are now visible.

I have added nomodeset to /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

and uncommented in /etc/default/grub;

```
GRUB_GFXMODE=640x480
```

---

