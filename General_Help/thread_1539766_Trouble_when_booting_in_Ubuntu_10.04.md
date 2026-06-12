---
title: "Trouble when booting in Ubuntu 10.04"
date: 2010-07-26
forum: General Help
---

### Post by Prince Valiant on 2010-07-26
Hello!

I'm running an Acer Aspire One D250-1958 with Ubuntu 10.04.  A while ago, the start up splash screen started running text as follows:  

```
acer-wmi; unable to detect available WMID devices [and then some numbers].
```

I followed the instructions on [this]("http://ubuntuforums.org/showthread.php?t=1233149") thread, and blacklisted acer-wmi.  Now, a new piece of text shows up:

```
skipping profile in etc/apparmor.d/disable  usr.bin.firefox
```

This would also occasionally show up previously before the blacklisting.  

Is there any way to prevent this from showing up when I try to boot?  The computer works fine, boot up just takes a little longer.

Thanks!

-Val

---

### Post by mikewhatever on 2010-07-27
Have you edited any grub configuration files? Can you post your /etc/default/grub.

---

### Post by Prince Valiant on 2010-07-29
No; to the best of my knowledge I've never edited this file.  Here you go:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
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

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Thanks for your help.

-Val

---

