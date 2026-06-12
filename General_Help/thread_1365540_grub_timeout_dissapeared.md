---
title: "grub timeout dissapeared"
date: 2009-12-27
forum: General Help
---

### Post by repsakkgn on 2009-12-27
after running some grub tools grub timeout dissapeared. grub just loads and waits for me to hit "enter". I'm running ubuntu 9.10
 here is my grub config
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=773"

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

---

### Post by Leppie on 2009-12-27
> **repsakkgn said:**
> after running some grub tools
could you be a bit more specific?

please [download and run this script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

---

### Post by repsakkgn on 2009-12-27
what was that script?? the result is the neverending 
"1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found
1.sh: 156: i++: not found"
 in the console...........

---

### Post by dcstar on 2009-12-27
> **repsakkgn said:**
> after running some grub tools grub timeout dissapeared. grub just loads and waits for me to hit "enter". I'm running ubuntu 9.10
 here is my grub config
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
**#GRUB_HIDDEN_TIMEOUT=0**
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=773"
........

I suggest that you remove that comment and then run update-grub.

---

### Post by repsakkgn on 2009-12-28
it didn't help.:confused:

---

### Post by dcstar on 2009-12-28
> **repsakkgn said:**
> it didn't help.:confused:

Read this and check your /boot/grub/grubenv file:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/462888](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/462888)

Also:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/447725](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/447725)

---

