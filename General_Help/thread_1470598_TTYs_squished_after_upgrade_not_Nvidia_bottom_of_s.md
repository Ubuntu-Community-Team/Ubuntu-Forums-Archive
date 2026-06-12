---
title: "TTYs squished after upgrade: not Nvidia bottom of screen problem"
date: 2010-05-03
forum: General Help
---

### Post by Buggin on 2010-05-03
After the 10.04 upgrade all my CTRL-ALT-F1-6 terminals are squished up at the top of the screen. it's as if the vertical was pushed all the way to the top. You can't read anything. Here's a picture of it. [http://imgur.com/7FKGo](http://imgur.com/7FKGo)

I'm running Nvidia binary drivers and everything seems to work great otherwise but I can't even find one person with this issue. I tried IRC already but no luck there yet. 

vga=795 is set in /etc/default/grub which is the correct res and depth

---

### Post by dcstar on 2010-05-03
> **Buggin said:**
> After the 10.04 upgrade all my CTRL-ALT-F1-6 terminals are squished up at the top of the screen. it's as if the vertical was pushed all the way to the top. You can't read anything. Here's a picture of it. [http://imgur.com/7FKGo](http://imgur.com/7FKGo)

I'm running Nvidia binary drivers and everything seems to work great otherwise but I can't even find one person with this issue. I tried IRC already but no luck there yet. 

vga=795 is set in /etc/default/grub which is the correct res and depth

Uncomment the GRUB_GFXMODE line and do an update-grub.

---

### Post by Buggin on 2010-05-03
I'll give that a shot when I get home(well actually I did it already but I'll reboot when I get home) and see how it goes... thanks

---

### Post by Buggin on 2010-05-03
that did not solve the problem... it exactly teh same...

I see the same issue on a VM I run but it just glitches to the top for a split second and is back to normal by the time i can do anything... i get no bootsplash or anything and no terminals... i'm about to uninstall plymouth and see what difference that makes

---

### Post by Buggin on 2010-05-03
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash "

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




thsi file makes it work for me... problem solved

---

### Post by superyounan1 on 2010-05-15
I have the same exact problem, but there is no grub.cfg file to work with.:
```
:/boot/grub$ ls
default        grubenv            menu.lst~          splashimages
device.map     installed-version  menu.lst.backup    stage1
e2fs_stage1_5  jfs_stage1_5       minix_stage1_5     stage2
fat_stage1_5   menu.lst           reiserfs_stage1_5  xfs_stage1_5

$ grep GRUB_GFXMODE *
<no results>

```

Anyone else with this problem? (Lucid)

---

