---
title: "Cannot turn off PC"
date: 2010-10-11
forum: General Help
---

### Post by jurco on 2010-10-11
Hi guys.
My ubuntu 10.04 doesnt want to turn off my PC (desktop) when I click turn off in the menu. I get no message, and I get no signs of higher system activity. This happens with turning off, rebooting, logging off user.
However I can do it from terminal with admin rights.

(Please do not advise me to create a launcher turning PC, I just want ubuntu works as it should be...)

thanks

---

### Post by dino99 on 2010-10-11
same problem here, report on launchpad to let devs know about that issue

---

### Post by TheAnachron on 2010-10-11
Guys can you tell me what the systemmonitor shows? 
Also check if there is anything in the system logs. /var/logs/sys

---

### Post by dino99 on 2010-10-11
> **TheAnachron said:**
> Guys can you tell me what the systemmonitor shows? 
Also check if there is anything in the system logs. /var/logs/sys

its a udev issue with some hardware

---

### Post by TheAnachron on 2010-10-11
I see, sorry then, was just trying to help!

---

### Post by jurco on 2010-10-12
I am thinking af upgrading to meerkat maybe it will help...

---

### Post by searchfgold6789 on 2010-10-12
I don't think this will help, but try adding to your partition's entry in etc/default/grub the line ```
acpi=force
```

---

### Post by jurco on 2010-10-13
hey dino99, do you have openoffice quickstarter enabled? When I exit the quickstarter turning off computer works fine

---

### Post by dino99 on 2010-10-13
> **jurco said:**
> hey dino99, do you have openoffice quickstarter enabled? When I exit the quickstarter turning off computer works fine

nope, as said above, blame acpi

---

### Post by jurco on 2010-10-19
hey searchfgold6789, I added acpi="force" at the end of my file /etc/default/grub so it loks like this
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

ACPI="FORCE"



then I ran update-grub but nothing changed in /boot/grub/grub.cfg so I dont know...

---

