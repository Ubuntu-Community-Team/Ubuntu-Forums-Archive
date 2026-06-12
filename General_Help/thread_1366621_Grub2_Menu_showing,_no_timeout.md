---
title: "Grub2 Menu showing, no timeout"
date: 2009-12-28
forum: General Help
---

### Post by ChrisGaeth on 2009-12-28
All of the sudden when my notebook boots it stays on the Grub2 menu screen. I have to select an option for it to boot into.  It acts like it does not have a default or the timeout is set to -1. I went through the grub file and ran update-grub. No change. Any ideas?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by ChrisGaeth on 2009-12-28
I found a workaround [http://xbmc.org/forum/showthread.php?p=466555]("http://xbmc.org/forum/showthread.php?p=466555").  I still would like the understand what changed.

---

### Post by ranch hand on 2009-12-28
> **ChrisGaeth said:**
> I found a workaround [http://xbmc.org/forum/showthread.php?p=466555](http://xbmc.org/forum/showthread.php?p=466555).  I still would like the understand what changed.
This a left over from earlier versions of grub1.97.  Your solution is fine.

What "grub file were you working with?  You are showing /boot/grub/grub.cfg.  This is silly to edit (besides being a pain).  It is over-written each time "sudo update-grub" is run.

You need to work in /etc/default/grub and /etc/grub.d/00_headers (in your case).  

The grub.d directory is key to most things.  There is a simple grub2 intro in my sig.

Use the second link I supply there for your future problems (if any) as it is the best you are going to find anywhere.

---

### Post by bcollignon on 2010-10-16
> **ChrisGaeth said:**
> I found a workaround [http://xbmc.org/forum/showthread.php?p=466555]("http://xbmc.org/forum/showthread.php?p=466555").  I still would like the understand what changed.

This worked for me; however there are other issues, like splash screens not working and resolutions, once changed in /etc/default/grub, not taking effect... strange.

---

