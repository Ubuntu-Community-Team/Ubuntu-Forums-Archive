---
title: "Deadlock when x starts"
date: 2009-08-24
forum: General Help
---

### Post by infurnus on 2009-08-24
I'm having an issue when GDM starts from inital boot my system dead locks - can't control+alt+backspace - can't switch to TTY - only thing it responds to is RSEIUB 

Issue: After booting normally as soon as gdm starts the graphics split into 4 sections and freezes totally. I cannot switch to a tty (control+alt+f2/f3/f4 etc all do nothing) I can alt+sysrq RSEIUB - it will respond to that. Short of doing an emergency shutdown it won't respond.

I have tried the recovery console to fix display issues & fix broken packages. Neither seem to help. I've also tried to `dpkg-reconfigure xserver-xorg`.

This started after trying to mount my NTFS partition - it gave me an error in ubuntu and suggested to run chkdsk. I ran chkdsk and it did delete some tables and appeared to fix something. However, next time I booted into ubuntu I started having the graphics problem.

I did run fschk which took about an hour and it as well did find issues and corrected them. BUT I still have my graphics freeze. It never makes it to login as it deadlocks before that. Since I don't have any access to tty's I don't really know where to go from here :*(

Version:9.04
Video Card: Radeon 9550
Processor:AMD Athlon XP 1800+
Arch: x86

Device Layout:
/dev/sdb1 - 227Gb NTFS Partition
/dev/sdb2 - 972Mb Swap
/dev/sdb3 - 56Gb Ext3 partition

This all worked until I ran chkdsk on the first partition because it wouldn't mount in ubuntu. 

The only (WW) in xorg are:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path

(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(WW) RADEON(0): Option "UseFBDev" is not used

any other infomation that would be helpful?

---

### Post by infurnus on 2009-08-25
Update: Fglrx cause a break in the package - as if I was persistent and alt+sys+K a bunch it would finally become responsive enough to switch to TTY1 where I could set vesa. However, I was never able to get 3d working with my ATI Radeon 9550.

Tried to dpkg-reconfigure -phigh but still never got it back to the way the liveCd works.

Final Solution: After days of messing with it finally just bit the bullet and reinstalled. Issue resolved.

---

