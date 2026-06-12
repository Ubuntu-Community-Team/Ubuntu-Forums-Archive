---
title: "Grub2 and the Kernel Menu"
date: 2010-03-03
forum: General Help
---

### Post by notahero on 2010-03-03
Hey, hope someone has an idea of what is going on here, as I have done a fair share of googling with no luck so far.

In an effort to try and speed up the boot time of Ubuntu 9.10 on my laptop I followed a few guides that had me adjusting my /etc/default/grub file and also changing my /etc/init.d/rc file.

I changed the different Timeout values in the grub file, and changed my Concurrency setting in the rc file. The boot up does feel speedier, but I am now presented with the Grub menu and asked to choose a kernel at each startup. I have reset the settings to their former versions, I have commented out different sections of the Timeouts, and I have attempted to disable the OS-Prober all to no avail. 

Any ideas?

I am running Ubuntu 9.10 Karmic Koala x64 as my only operating system, my Grub version is 1.97~beta4 and if I press e in the menu screen it does show a recordfail=1.

My /etc/default/grub file is as shown...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

My kernel choices are the most current linux kernel, the most current linux kernel with recovery mode, and two seperate memtest86+ options. If I click enter it takes me straight into Ubuntu normally.

---

### Post by notahero on 2010-03-03
I have tried following some of the errors section in the Grub2 wiki such as deleting out the no-floppy inside the /boot/grub/grub.cfg but I am still having the issue of the Kernel Menu always showing up at boot. Running out of options, may soon just reinstall 9.10.

---

