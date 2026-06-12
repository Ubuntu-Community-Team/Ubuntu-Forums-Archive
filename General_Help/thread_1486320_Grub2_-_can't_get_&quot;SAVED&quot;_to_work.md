---
title: "Grub2 - can't get &quot;SAVED&quot; to work"
date: 2010-05-17
forum: General Help
---

### Post by yonkiman on 2010-05-17
Grub2 always boots the first item on the grub menu.  I edited my 
/etc/default/grub to this:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=SAVED
GRUB_SAVEDEFAULT=true
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=799"

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

Then ran update-grub, but it still awlays boots from the first menu.  Any ideas what else I should look at?

[INDENT]$ uname -a
Linux Lucid-Office 2.6.32-22-generic #33[/INDENT]

-Fred

---

### Post by efflandt on 2010-05-17
Case (upper/lower) is important in Linux.  This works for me in 9.10 or 10.04 to default to whatever I booted last (I commented out the original line and replicated it with saved):

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved

Not even sure what GRUB_SAVEDEFAULT=true does because I do not use that.

PS: GRUB_CMDLINE_LINUX_DEFAULT is defaults for normal kernels and GRUB_CMDLINE_LINUX is defaults for ALL kernels including (recovery).  So by listing splash in both, splash ends up listed twice for normal kernels.  Do you really want splash for recovery kernels?

---

### Post by yonkiman on 2010-05-18
> **efflandt said:**
> Case (upper/lower) is important in Linux....  
GRUB_DEFAULT=saved

Of course!  That fixed it.  Thanks.

---

