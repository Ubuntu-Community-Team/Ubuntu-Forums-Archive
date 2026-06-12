---
title: "Screen brightness resets to max when starting Firefox (also on reboot)"
date: 2012-10-11
forum: General Help
---

### Post by BigHeadCreations on 2012-10-11
What I'm using:
Ubuntu 12.04
Sony Vaio PCG 61112L  (about 2 year old laptop)
nvidia graphics

[B]Problem:  My screen brightness resets to max brightness when:
start Firefox
in Google Chrome when I watch a video
Computer reboots or awakes from sleep (open the lid)[/B]

My problem is that with the recent Firefox update, **everytime I start firefox my screen brightness resets to maxium**.  I have always had the problem of the brightness resetting to max on reboot, but I thought this problem was not a big deal because it doesn't interrupt my workflow.  However the brightness resetting to max when opening Firefox is a big deal to me.  Does anybody else have this problem?  

BTW, **my function f5/f6 keys DO WORK**.  To get them to work I followed this solution: [http://ubuntuforums.org/showthread.php?t=1966635&highlight=sony+vaio+brightness+resetting](http://ubuntuforums.org/showthread.php?t=1966635&highlight=sony+vaio+brightness+resetting)

Other info:
my /etc/X11/xorg.conf looks like 
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option        "RegistryDwords" "EnableBrightnessControl=1"
   SubSection    "Dsiplay"
    Depth    24
   EndSubSection
EndSection

Section "InputClass"
    Identifier    "RFMouse"
    MatchProduct    "2.4G RF Keyboard & Mouse"
    Option        "ConstantDeceleration" "10"
EndSection

```my /etc/default/grub    looks like this:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_sleep=nonvs"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Also doing this also adjusts the brightness just fine (if I have sudo privileges): 
```

echo x > /sys/class/backlight/nvidia_backlight/brightness

```Any idea on how to fix this?

Thanks

---

### Post by claracc on 2012-10-12
This is a known bug.

You can preserve your brightness settings as is addressed in this link: [http://thanhsiang.org/faqing/node/180](http://thanhsiang.org/faqing/node/180)

---

### Post by BigHeadCreations on 2012-10-12
> **claracc said:**
> This is a known bug.

You can preserve your brightness settings as is addressed in this link: [http://thanhsiang.org/faqing/node/180](http://thanhsiang.org/faqing/node/180)

Thanks for the link.  However that looks like it will only fix the problem of brightness going to max on a reboot.   Is there a way to fix the brightness not going to maximum when I start Firefox?

---

### Post by BigHeadCreations on 2012-10-13
Anybody else run into this problem?

---

### Post by BigHeadCreations on 2012-10-20
Here is some new evidence!

I just logged in using 'Unity 2D' instead of just regular 'Unity' and all of my problems are solved!!  Any idea why this would be so and how to replicate it in regular 'Unity'??

Thanks.

---

