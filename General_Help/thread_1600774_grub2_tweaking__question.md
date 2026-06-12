---
title: "grub2 tweaking  question"
date: 2010-10-19
forum: General Help
---

### Post by NikitaUtiu on 2010-10-19
I have been doing some tweaking to the /etc/default/grub recently, but the results are not as expected.
This is my file:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=769"

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
```Iwant  have the menu hidden unless I press shift.I have also changed the GRUB_HIDDEN_TIMEOUT_QUIET to false because I want to get a counter even if the menu isn't displayed... but I don't get it, I go directly into the menu. And since I installed grub2, the splash screen with the ubuntu logo has been written in Courier font.

So how do I  hide the menu and display the timer and make the logo look normal again ?

Thanks, NikitaUtiu.

---

### Post by NikitaUtiu on 2010-10-19
Well I have fixed the "not hiding the menu problem", but not the way I'd have wanted to. 
I cahnged 
GRUB_TIMEOUT=-1 
to 
GRUB_TIMEOUT=5

So now when I press shift I am prompted with a menu that also counts down. 
Any alternative ?:confused:

---

### Post by NikitaUtiu on 2010-10-20
I fixed the splash image by removing it. I just changed the line
```
GRUB_CMDLINE_LINUX="splash quiet vga=769"
```
to 
```
GRUB_CMDLINE_LINUX="splash quiet"
```

Still no timer.

---

