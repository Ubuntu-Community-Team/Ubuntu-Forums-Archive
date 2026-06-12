---
title: "update-grub exited with value 127 (Update Trouble)"
date: 2010-07-16
forum: General Help
---

### Post by dreamsR4living on 2010-07-16
Since 6 weeks or so, updates of linux-image refuse to install in apt due to a problem with GRUB. I don't see anything unusual in /etc/default/grub. I did also try a clean install of grub and linux-image-generic, but it didn't help.

I am using Ubuntu 10.04 i386. I have posted the output of sudo dpkg --configure -a and /etc/default/grub below.

Who can tell me how to fix this?

```
sebastiaan@sebastiaan-desktop:~$ sudo dpkg --configure -a
[sudo] password for sebastiaan: 
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu6) ...
/etc/default/grub: 9: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-22-generic (2.6.32-22.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-generic
 grub-pc
 linux-image-2.6.32-22-generic
 linux-image
sebastiaan@sebastiaan-desktop:~$ 

```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash nomodeset video=uvesafb:mode_option=1280×1024-24,mtrr=3,scroll=ywrap”
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280×1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by dreamsR4living on 2010-07-28
I just did a reinstall, which of course fixed my problem. It's a pity that nobody knows a solution...

---

### Post by Laysan_A on 2010-11-08
@dreamsR4living
You've long ago fixed this by reinstalling. I think you lost a quotation mark after the word splash in your grub file.

Anyway, I had the same trouble. It was a radeon.modeset I had put in grub at the behest of the fine people at cairo-dock. I deleted the offending entry and ran update-grub, then "apt-get install -f" and it's fine now.

(you should have bumped a couple times:))

---

