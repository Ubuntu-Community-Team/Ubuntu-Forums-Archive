---
title: "Just realized that Plymouth exists, but I never see it."
date: 2011-01-22
forum: General Help
---

### Post by ninjaaron on 2011-01-22
I want a fancy splash-screen. What do I do?

P.S. I have edited /etc/default/grub to calibrate my touch-screen... I feel like that might be related... I dunno. Anyway, this is what it says:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0x0eef:0x725e:0x40"
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

---

### Post by andymorton on 2011-01-22
```
sudo -s
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u
```


Put the above into the terminal and the Plymouth theme will show on start-up

andy :)

---

### Post by ninjaaron on 2011-01-23
The last command output this:

```
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
.: 6: Can't open /scripts/casper-functions
```

Needless to say, I still don't see plymouth.

---

### Post by dcstar on 2011-01-23
> **ninjaaron said:**
> The last command output this:

```
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
.: 6: Can't open /scripts/casper-functions
```

Needless to say, I still don't see plymouth.

Try the basic command for initramfs:

```
sudo update-initramfs -u -k all
```

---

