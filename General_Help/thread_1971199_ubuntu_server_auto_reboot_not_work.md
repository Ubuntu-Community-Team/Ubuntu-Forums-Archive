---
title: "ubuntu server auto reboot not work"
date: 2012-05-02
forum: General Help
---

### Post by knutarn on 2012-05-02
Hey. I struggle with my ubuntu server for a while now.

When the server start or i use sudo reboot, then comes the photo here, and everything works and it starts so good

But if the server reboot by itself (crontab and use shutdown -r now or reboot) then stops at the photo here. then wait there until I press enter

[IMG]http://3.bp.blogspot.com/-hwcHsDGgdk0/Truor-PwrEI/AAAAAAAAABQ/ECBKQPbE_dQ/s1600/ubuntu-debian.png[/IMG]
PS: is not my picture. found it on Goolge, but is almost same'

OS:Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64)

Here is my GRUB

[PHP]# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 
GRUB_DEFAULT=0 
#GRUB_HIDDEN_TIMEOUT=0 
GRUB_HIDDEN_TIMEOUT_QUIET=true 
GRUB_TIMEOUT=2 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2&--#62; /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="text" 
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
#GRUB_DISABLE_RECOVERY="true" 
# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1"[/PHP]

what is wrong? and have tested and remove the keyboard. but not work

---

### Post by knutarn on 2012-05-02
any won now?

---

### Post by Coder68 on 2012-05-10
Google is your friend. ;)

[http://askubuntu.com/questions/13730/how-can-i-schedule-a-nightly-reboot](http://askubuntu.com/questions/13730/how-can-i-schedule-a-nightly-reboot)

---

