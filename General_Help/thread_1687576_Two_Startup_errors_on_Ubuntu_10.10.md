---
title: "Two Startup errors on Ubuntu 10.10"
date: 2011-02-14
forum: General Help
---

### Post by manish12345 on 2011-02-14
i have 2 errors while loading ubuntu 10.10:

i) VGA=788 is deprecated. Use gfpayload = 800x600x16, 800x600 before linux command instead

ii) An error occurred while mounting /media/sdb1. Press S to skip.....

For error (i) I tried changing parameters in Startup-Manager but it still persists

Error (ii) is a result of my fiddling with fstab, psydm to auto mount drives on start up which eventually i solved through autofs however the error message is still coming..i am pasting the contents of /etc/fstab here please suggest what to do..```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                          /proc           proc     nodev,noexec,nosuid          0  0  
/dev/sdb1                     /host           fuseblk  defaults                     0  0  
/dev/sda1                     /media/WINDOWS  ntfs-3g  defaults,locale=en_US.UTF-8  0  0  
/dev/sda3                     /media/sda3     ntfs-3g  defaults                     0  0  
/dev/sda5                     /media/sda5     ntfs-3g  defaults                     0  0  
/dev/sdb1                     /media/sdb1     ntfs-3g  defaults,locale=en_US.UTF-8  0  0  
/dev/sdb5                     /media/sdb5     ntfs-3g  defaults                     0  0  
/dev/sdb6                     /media/sdb6     ntfs-3g  defaults                     0  0  
/dev/sdb7                     /media/sdb7     ntfs-3g  defaults                     0  0  
/host/ubuntu/disks/root.disk  /               ext4     loop,errors=remount-ro       0  1  
/host/ubuntu/disks/swap.disk  none            swap     loop,sw                      0  0
```

---

### Post by manish12345 on 2011-02-14
Any one? Please...

Here's my grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=788"

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

