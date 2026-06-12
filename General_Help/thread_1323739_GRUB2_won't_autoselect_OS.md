---
title: "GRUB2 won't autoselect OS"
date: 2009-11-12
forum: General Help
---

### Post by koolcracker on 2009-11-12
Only once of the many times I have booted Ubuntu since upgrading to karmic has there bee the 10 second countdown at the GRUB followed by an automatic selection. I have tried varying the time, and I believe everything in my file is set up right, but GRUB just won't automatically boot into Ubuntu for me after the timeout.

Here are the contents of /etc/default/grub

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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

I did run update-grub, it didn't work. I am really hoping someone may be able to shed some light on this as I do not particularly care for babysitting my bootup every step of the way. Thanks for your time!

---

### Post by bashphoenux on 2009-11-12
can you post for menu.lst file as attachment file here?

---

### Post by sudulo on 2009-11-12
> **bashphoenux said:**
> can you post for menu.lst file as attachment file here?

Apparently, there is no menu.lst anymore. It has been substituted by /etc/default/grub , being "grub" a text file you can edit with gedit, as long as you are root... :p

After changing this file, you must execute "update-grub", of course. That reminds me of the long forgotten days of LILO. Is grub2 the new LILO? X')

---

### Post by module0000 on 2009-11-12
Please post your /boot/grub/grub.cfg, that's where the final default/timeout values will be located.  /etc/default/grub is just one of many sources of data used to generate the final /boot/grub/grub.cfg

Also, if you think something was tampered with and want to "redo" your grub2, run the following sequence of commands:

sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo grub-install /dev/sda

Replace /dev/sda with your proper boot device if /dev/sda isn't applicable in your setup.

EDIT: If your first boot item on the list is a label, or not a bootable options, having DEFAULT=0 will cause you to not boot automatically. DEFAULT=0 translates to "boot the first item in the list as default".  Forgot to mention that.

---

### Post by hwttdz on 2009-11-12
You need sudo permissions to run update-grub.  Try "sudo update-grub" then try rebooting (only if the command worked).

---

