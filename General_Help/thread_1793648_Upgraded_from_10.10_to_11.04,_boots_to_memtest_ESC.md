---
title: "Upgraded from 10.10 to 11.04, boots to memtest ESC not working"
date: 2011-06-29
forum: General Help
---

### Post by blm14 on 2011-06-29
Hey everyone! So I have a machine that was running 10.10 and I updated it to 11.04 and now when I reboot I am taken directly into memtest. Any attempt to hit esc during boot is ignored and no matter what I just go into memtest.

Here is /etc/default/grub from my boot drive

```

ubuntu@ubuntu:/media/c8e24038-87b7-4a9a-87e0-11de250e3f4b$ cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I am booting now from a 10.10 USB stick and I can access my boot drive so if I need to change stuff I can. Halp!

---

### Post by drs305 on 2011-06-29
We may need to see your boot files, but for now try holding down the SHIFT key during boot. That should display the Grub2 menu and perhaps you will be able to select your OS.

If not, please click the "BIS" link in my signature line. That will take you to the "Boot Info Page". Download, extract and run the boot info script, and post the contents of RESULTS.txt so we can review what's happening at boot.

---

