---
title: "grub problems on kernel upgrade"
date: 2011-07-16
forum: General Help
---

### Post by adempewolff on 2011-07-16
With the most recent kernel update I ran into the same problem discussed in this post([link]("http://ubuntuforums.org/showthread.php?t=1804405")): configuration of the kernel didn't complete because there was a syntax error in line 25 of grub.cfg.  I followed the instructions in that thread and fixed that syntax error, which appeared to fix the problem (the configuration of the kernel actually completed. But when I looked closer, I saw that there are still grub errors, and that when I restart, the newest kernel is still 2.6.38-8-generic rather than 2.6.38-10-generic.  I would appreciate any advice on how to get my grub files sorted out.

Reinstallation log:
```
(Reading database ... 160929 files and directories currently installed.)
Preparing to replace linux-image-2.6.38-10-generic 2.6.38-10.46 (using .../linux-image-2.6.38-10-generic_2.6.38-10.46_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-10-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Preparing to replace linux-image-generic 2.6.38.10.25 (using .../linux-image-generic_2.6.38.10.25_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-10.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-10.46 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Fedora release 13 (Goddard) on /dev/sda2
Found Ubuntu 10.10 (10.10) on /dev/sda8
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 100
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
Setting up linux-image-generic (2.6.38.10.25) ...

```

/etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1280x800-24<<,mtrr=3,scroll=ywrap"
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
GRUB_GFXMODE=1280x800 ## this is the line I modified to fix the first error it was "GRUB_GFXMODE=>>1280x800-24<<" before ##

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I've attached the /etc/grub.d/* files as text files since they are so long.

---

### Post by adempewolff on 2011-07-16
here are the rest of the grub.d files:

---

### Post by dino99 on 2011-07-16
sudo dpkg-reconfigure grub-pc

---

### Post by adempewolff on 2011-07-16
I suspected that might be the quickest way.  I'm getting this prompt though which I have never seen before:

```
Package configuration




 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; The following Linux command line was extracted from /etc/default/grub or  &#9474; 
 &#9474; the `kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is  &#9474; 
 &#9474; correct, and modify it if necessary.                                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Linux command line:                                                       &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; _________________________________________________________________________ &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               




```

As far as I can tell, the field where this command line is has nothing in it.  Any thoughts?

---

### Post by dino99 on 2011-07-16
why worrying ? open synaptic to purge all the installed grub packages, then (in a raw) reinstall grub-pc & grub-common

---

### Post by adempewolff on 2011-07-16
It looks like that did the trick. Thanks!

For those who are curious, here is the two (or three, counting the original change I made) differences between the old and new grub files:

#1  hidden timeout commented out
old:
```
GRUB_HIDDEN_TIMEOUT=0
```

new:
```
#GRUB_HIDDEN_TIMEOUT=0
```

#2  different kernel parameters
old:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1280x800-24<<,mtrr=3,scroll=ywrap"
```

new:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

#3 original changes I made to GRUB_GFXMODE, now commented out

original old:
```
GRUB_GFXMODE=>>1280x800-24<<
```

modified old:
```
GRUB_GFXMODE=1280x800
```

new:
```
#GRUB_GFXMODE=640x480
```

---

### Post by Paloseco on 2011-07-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798980](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/798980)

# sudo chmod a-x /etc/kernel/header_postinst.d/nvidia-common
# sudo chmod a-x /etc/kernel/postinst.d/nvidia-common
Upgrade kernel headers and image.

---

### Post by cmh8133 on 2012-01-09
Thanks to suggested  dpkg-reconfigure grub-pc fixed it for
ubuntu servers on VMware that are using do-release-upgrade from 10.10 to 11.04.

ALSO this is damaging xorg so we get the z'd out screen.

cmh

---

