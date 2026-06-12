---
title: "Ubuntu 9.10 And grub issue..... need help please."
date: 2009-10-30
forum: General Help
---

### Post by Solorflare on 2009-10-30
I have put the 9.10 version on my laptop, and when it boots up my cpu fan refuses to work and my computer gets hot and shuts down, unless I use the edit option when grub loads up and put in both noapic and acpi=off...

Is there a way to make this permanent as I have to do it every time I boot the computer.

I have tried editing the grub.cfg file but it refuses to let me in.
Is there another way?

Thanks.

---

### Post by Herman on 2009-10-30
:D You're right, we're not supposed to edit /boot/grub/grub.conf directly.
We can edit another file though, it's the one called  /etc/default/grub and it will be scanned the next time we run grub-mkconfig and the changes will then be added to our new grub.cfg. 
```
gksudo gedit  /etc/default/grub
``````
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=795 [COLOR=Purple]noapic acpi=off[/COLOR]"

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
``````
sudo grub-mkconfig -o /boot/grub/grub.cfg
```Source: [TWEAKING GRUB 2]("http://www.drlock.com/blog/2008/07/11/tweaking-grub-2/") - Dr.Lock

---

### Post by Solorflare on 2009-10-30
Thank you that worked.
:)

Cool

---

### Post by Herman on 2009-10-30
:D Thanks for the positive feedback, good work! Enjoy your Ubuntuing and GRUB2ing! :D

---

