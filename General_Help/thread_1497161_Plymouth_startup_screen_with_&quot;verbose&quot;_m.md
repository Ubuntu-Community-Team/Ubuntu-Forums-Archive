---
title: "Plymouth startup screen with &quot;verbose&quot; message logs?"
date: 2010-05-30
forum: General Help
---

### Post by CDrewing on 2010-05-30
Hi there,

I got plymouth working with my NVIDIA - finally. But as I see a beloved boot option does not work: "verbose". Normally, booting with "verbose splash" in Grub you should get all the fancy boot messages in a text box under the Ubuntu logo. BUt changing from "quiet splash" to "verbose splash" (and updating grub) does not change anything.

Can anyone help? Or is Plymouth just not prepared for showing text messages?

Here's my /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX="vga=795"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Best regards
Christian

---

