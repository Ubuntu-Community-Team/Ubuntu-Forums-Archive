---
title: "/dev/pty devices not present"
date: 2009-12-14
forum: General Help
---

### Post by nicksvt on 2009-12-14
It seems on my install of Ubuntu 9.10, there are no /dev/pty* devices for use on the 2.6.31-15-generic kernel, which I need for a script which worked before on Ubuntu 8.x.  

I believe this is caused by a kernel change, but I am wondering if anyone knows a workaround for it on ubuntu, or a similar alternative.

---

### Post by nicksvt on 2009-12-14
To follow up, this appears to be something that is controlled by the kernel setting: CONFIG_LEGACY_PTYS.  This setting controls whether the kernel supports BSD-style pseudo-terminals.

When I looked under the kernel headers (/usr/src/linux-headers-`uname -r`/drivers/char/Kconfig) this setting appeared to be set to "y" by default.  Does this mean that this is the setting that was used to compile the kernel that I am using?

Also, is there any way to enable this setting without recompiling the kernel?  Since this seems to be a Makefile config-flag, I would expect that the only way to support BSD-style pseudo-terminals would be to recompile the kernel.

---

### Post by niftyshorts on 2010-03-12
I have the same problem.  I'm running Ubuntu Desktop 9.10 64 bit.  How the heck do you enable legacy PTY devices.  I can get it working on 32 bit by editing /boot/grub/menu.lst, but in 64 bit there is no such file.

Someone please help!!!

---

### Post by niftyshorts on 2010-03-12
Figured it out.  The problem was 9.10 now runs grub2 instead of grub.

All you need to do is vi /etc/default/grub

Change the line: 

GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX="pty.legacy_count=256"

Where 256 is the number of pty legacy devices you require.  Dunno what I'd do without Google. :p

---

### Post by niftyshorts on 2010-03-12
Oh yeah - and then reboot!

---

### Post by leonardinux on 2010-11-25
Ok, find a trick: I've setted up the paramenter pty.legacy_count with a wrong number (10).

LeonardinuX

---

