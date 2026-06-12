---
title: "How to interrupt Grub"
date: 2011-08-01
forum: General Help
---

### Post by Wim Sturkenboom on 2011-08-01
Trying to help somebody on the forum with a question; I like to interrupt grub at boot so I can modify the parameters. This system is a standard single boot setup with Ubuntu 10.04 only. Pressed <esc> as well as <space> during boot but it does not pick it up and boots straight into Ubuntu.

**[COLOR="Blue"]So what is the key / key combination?[/COLOR]** Note that I don't want to (or can't) modify the default settings to set a timeout (that will probably work).

For completeness, my grub configuration
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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
```

---

### Post by linuxman94 on 2011-08-01
The correct key should be shift.  Just hold it down while your system boots.

---

### Post by Wim Sturkenboom on 2011-08-01
Great, works

Thanks a lot

---

