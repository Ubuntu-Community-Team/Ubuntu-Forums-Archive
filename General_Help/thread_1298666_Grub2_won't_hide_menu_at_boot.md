---
title: "Grub2 won't hide menu at boot"
date: 2009-10-23
forum: General Help
---

### Post by richierich1986 on 2009-10-23
Hello,

I'm using Ubuntu 9.10 Karmic Koala RC since yesterday.
I did a fresh install and it is the only OS on my computer.

I have a problem with grub2:

It will not stop showing the menu when I boot the system,
which wouldn't be that bad if it wasn't for the fact that it
won't show a time-out as well.

I tried editing the /etc/default/grub file, following the guide
I found for grub2, and afterwards I 'sudo update-grub', but
then when I reboot, the menu just keeps coming up again 
and won't continue to boot until I make a choice by pressing
enter, every single time. You can guess this gets annoying
after a while.

Can anyone who did manage to keep his menu from showing
at boot, show me what their /etc/default/grub file looks like,
so I can copy your settings and see if it works for me?

If that doesn't work, it'll probably just be a bug in grub2, but
since I haven't read about anyone else having this problem,
maybe I didn't get something right in the file.

Anyway, thanks to anyone willing to help me with this!

---

### Post by grnqrtr on 2009-10-28
I'm having problems with the grub 2 menu also.  I followed some instructions the ubuntu grub 2 wiki and I still can't get the menu to hide at startup.  Mine does however countdown and select the default OS.  Here is my etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

**EDIT**
I just got my menu to hide.  I changed GRUB_TIMEOUT to "0".  I figured that the way it was before would have hidden the menu and given me 3 seconds to press escape, but instead it showed the menu and gave me 3 seconds to pick.

Maybe if your still having trouble you should post your /etc/default/grub so that everyone can help you.

---

### Post by ario on 2010-02-12
Me too! I cant hide the menu. :(
my grub.cfg file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=12
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=791"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

---

### Post by wojox on 2010-02-12
No problems here:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 splash quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

---

