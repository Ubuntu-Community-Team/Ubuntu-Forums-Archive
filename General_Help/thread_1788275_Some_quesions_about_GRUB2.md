---
title: "Some quesions about GRUB2"
date: 2011-06-22
forum: General Help
---

### Post by Lucas Malor on 2011-06-22
In GRUB2, is there a way to:

[LIST=1]
[*]change font size
[*]add a simple line as divider
[*]set refresh rate
[/LIST]
?

---

### Post by dino99 on 2011-06-22
all you need to know below, following the grub2 link :)

and startup-manager may help about font size

---

### Post by Lucas Malor on 2011-06-22
I already read the guide, and I found nothing about. And I don't want to install another packages for this :)

---

### Post by dino99 on 2011-06-22
have some doubt, this guide is complete. And what about your 3) request ? (what do you want/need to refresh ?)

---

### Post by Lucas Malor on 2011-06-22
Well, I'm quite sure.

[LIST=1]
[*] The only way I found to change font size is to use grub-mkfont, but it  doesn't work with the default font unicode.pf2 because grub-mkfont  doesn't support .pf2 fonts (!)
[*]I found no way to add a simple dividing line. On the contrary, for what I remember, you was able to add it in GRUB1
[*]for refresh rate, I mean a CRT monitor refresh rate. With GRUB_GFXMODE you can set resolution and color depth, but not refresh rate. I want to set it to avoid monitor recalibration during Ubuntu startup.
[/LIST]

---

### Post by dino99 on 2011-06-22
refresh rate for CRT is inserted into xorg.conf, nothing related to grub.

---

### Post by oldfred on 2011-06-22
I like spacer lines, but only know how to do it as part of manual entries in 40_custom.

I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

This in 40_custom is a blank line:

menuentry " " {
set root= 
}

I usually add this also as I often miss hitting f12 and choosing a different boot device:

menuentry "Reboot" {
    reboot
}

I often add my own entries to boot partitions, so I do not have to run update-grub.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

And if you turn off all the other scripts you are just about back to the old menu.lst that you manual maintain in 40_custom or 06_custom etc.

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

---

### Post by Lucas Malor on 2011-06-23
I read drs305's thread too... and instead of a dividing line I start to think it's better to put recovery and memtests in a submenu. Thank you anyway.

---

### Post by Lucas Malor on 2011-06-27
Ok... the original font used by GRUB seems to be [unifont.bdf]("http://unifoundry.com/unifont.html"), but its size is 16 and can't be changed. I tried to use the ttf, with rough results.

---

