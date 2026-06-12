---
title: "editing grub file"
date: 2010-08-22
forum: General Help
---

### Post by f6e9a on 2010-08-22
okay i have to edit grub etc/default file 

but when i open it, it is a read only file (i have to put "i915.modeset=1" in it )

i think  i need to do it through the terminal 

any help 
:D

---

### Post by surfer on 2010-08-22
just in case, here is my [FONT="Courier New"]/etc/default/grub[/FONT] :


```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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

i did not touch it since the last reinstall.

---

### Post by anirudhtomer on 2010-08-22
haven't you heard the term "root user"?
sudo gedit /etc/default/filename will do it for you.

---

### Post by f6e9a on 2010-08-22
mine looks just like that but i cant make changes i need to know how too and thanks for the back up

---

### Post by oldfred on 2010-08-22
With graphical apps it is preferred to use gksudo.

gksudo gedit /etc/default/grub

---

