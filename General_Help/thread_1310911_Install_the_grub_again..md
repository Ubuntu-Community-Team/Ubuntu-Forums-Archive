---
title: "Install the grub again."
date: 2009-11-02
forum: General Help
---

### Post by praveenthivari on 2009-11-02
I had triple booted win7, ubuntu & Kubuntu and grub2 had made Ubuntu as default OS. I have seen that editing grub2 to change default OS is difficult so I changed it from Win 7 with EasyBCD but that didn't recognize my Linux OS's. So, I am trying to get back the grub to boot the system.
How do I do it.

---

### Post by P4man on 2009-11-02
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to item 12 on how to reinstall grub2 from a live cd. The rest may help you in modifying your grub.

A much easier way to reconfigure grub2 is installing startup manager from the repo's. It lets you pick the default OS and timeout and stuff with no fuzz, just a GUI.

---

### Post by praveenthivari on 2009-11-02
> **P4man said:**
> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll down to item 12 on how to reinstall grub2 from a live cd. The rest may help you in modifying your grub.

A much easier way to reconfigure grub2 is installing startup manager from the repo's. It lets you pick the default OS and timeout and stuff with no fuzz, just a GUI.

Am using Karmic and startup manager doesn't work in it.

---

### Post by P4man on 2009-11-02
> **praveenthivari said:**
> Am using Karmic and startup manager doesn't work in it.

Startup manager supports grub2. Its seems to run fine here (karmic as well) and correctly reads my grub settings (havent tried changing yet though).

---

### Post by drs305 on 2009-11-02
StartUp-Manager doesn't support all the options in Grub 2, but it supports the main ones. These include default OS, timeout, and a few others. It will also modify the "GRUB_CMDLINE_LINUX=" line for splash and text during boot, although if either of these is on the "GRUB_CMDLINE_LINUX_DEFAULT=" line it will not change the values there. 

It doesn't seem to be able to handle the actual splash images, nor set the Grub 2 menu resolution. It can set the system resolution with the "vga=" option but Grub 2 notes this is deprecated during the boot.

---

### Post by twrock on 2009-11-02
So why if it is "grub2" does it say it is 1.97 beta 4 when it boots? I would have assumed Ubuntu was not using a beta version and I also would have assumed grub2 is version 2. I'm so confused.:(

---

### Post by praveenthivari on 2009-11-02
> **P4man said:**
> Startup manager supports grub2. Its seems to run fine here (karmic as well) and correctly reads my grub settings (havent tried changing yet though).

It reads the grub settings correctly but doesn't change anything. 
I tried at the very beginning before resorting to EasyBCD and it didn't for me.

thanks for that link I had seen that link but had not read completely.

---

### Post by drs305 on 2009-11-02
> **praveenthivari said:**
> It reads the grub settings correctly but doesn't change anything. 
I tried at the very beginning before resorting to EasyBCD and it didn't for me.

thanks for that link I had seen that link but had not read completely.

It will change the things I mentioned in my previous post. Open /etc/default/grub in a text editor as root. Then open StartUp-Manager. As soon as one of the mentioned options is changed in SUM it is reflected in /etc/default/grub. Of course, you have to run "sudo update-grub" for the changes to be incorporated in the menu.

@twrock

The devs put GRUB 2 into the Karmic pre-releases because of the advantages of G2. GRUB 2 (1.97) was officially released within a couple of days of the Karmic rollout. GRUB 2 is a universal bootloader and not tied specifically to Ubuntu. The Ubuntu repositories will assumedly move from the 1.97 beta to the final product.

As a historical note, Grub legacy was version 0.97 - it never was 1.0, so we can probably expect GRUB 1.97 (aka GRUB 2) to be with us for quite a while without seeing a 'true' GRUB 2.0

---

