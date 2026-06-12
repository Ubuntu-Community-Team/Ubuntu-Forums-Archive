---
title: "Need to configure GRUB"
date: 2012-07-24
forum: General Help
---

### Post by Hungry Man on 2012-07-24
I'm running Ubuntu 12.04 and Windows 7 in dual boot. I misconfigured by /etc/default/grub file and can't boot into Windows.

Can someone post their grub file from a dual boot so I can get in?

---

### Post by NikTh on 2012-07-24
Hi , 
i don't think that /etc/default/grub has something to do with your windows entry.. 

Please open a terminal and do ```
sudo update-grub
``` give the resutls here.

Thanks

---

### Post by Hungry Man on 2012-07-24
It *would* show Windows but grub doesn't load. The timeout limit is messed up or something so it skips it.

Trust me, the issue is in /default/grub.

---

### Post by vasa1 on 2012-07-24
> **Hungry Man said:**
> I'm running Ubuntu 12.04 and Windows 7 in dual boot. I misconfigured by /etc/default/grub file and can't boot into Windows.

Can someone post their grub file from a dual boot so I can get in?
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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
Hope this helps

---

### Post by Hungry Man on 2012-07-24
It should, thanks.

---

