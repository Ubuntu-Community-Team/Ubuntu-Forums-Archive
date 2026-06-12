---
title: "GRUB2 boots into my default OS even after I've pressed a keyboard key"
date: 2011-02-10
forum: General Help
---

### Post by didibus on 2011-02-10
Hi,

I'm dual booting ubuntu 10.10 and Windows 7. I have GRUB2 working in the sense that when I start my computer, I see the GRUB2 menu appear, and it is listing all of my OS.

My problem is that, there is a 10 second count down that is showing, and if I don't manually select an entry, once the countdown gets to 0, it boots into my default OS. This works fine, but, if I press a key during the countdown, I see the countdown going away, but, somehow, its as if it was still counting down, because if I spend to much time making my selection to boot into another OS, GRUB2 will boot into the default OS.

To recap: When inside the grub2 menu, I want that when I press a key, GRUB2 will remain in the GRUB2 menu for as long as I don't press enter on one of the selected entry. Instead, it seems that it'll eventually just boot into the default OS even though I pressed a key.

Thank You.

P.S.: I tried setting GRUB_TIMEOUT=-1 , and yet, even though no counting appears now, it still boots into the default OS after a certain amount of time.

======================
Here is my etc/default/grub file content:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0

# If set to true this setting will automatically set the last selected OS from # the menu as the default OS on the next boot.
# No commands need be run to set the default OS.
# Any time a menu entry is manually selected from the GRUB 2 menu, it becomes # the default OS.
# This option currently does not work if your /boot directory resides on an LVM #partition or RAID
GRUB_SAVEDEFAULT=true

GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

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

---

### Post by labinnsw on 2011-02-13
Here is my file. Not sure if it is anything, but note two lines.

```
#GRUB_HIDDEN_TIMEOUT="3"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="0"
[B]#GRUB_HIDDEN_TIMEOUT="3"
GRUB_HIDDEN_TIMEOUT_QUIET="true"[/B]
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

#GRUB_DISABLE_OS_PROBER="false"
GRUB_SAVEDEFAULT="false"
export GRUB_COLOR_NORMAL="white/black"
export GRUB_COLOR_HIGHLIGHT="black/light-gray"
```

I would also like to recommend [Grub Customizer]("https://launchpad.net/grub-customizer") for working with grub2

---

### Post by grahammechanical on 2011-02-13
It seems to me that GRUB is doing what it is designed to do. You want it to do something that it is not designed to do. You could try putting your request to the GRUB developers. A press any key to halt count down feature. You could increase the timeout period to 30 seconds or longer. Personally there are many times that I just want to switch on my machine and let it load to my standard Ubuntu login screen without my interaction and in a minimum of time. GRUB2 works fine for me.

I certainly recommend the Grub Customizer utility. Excellent program. Made modifying Grub easy and painless.

Regards.

---

### Post by labinnsw on 2011-02-13
> **grahammechanical said:**
> It seems to me that GRUB is doing what it is designed to do. You want it to do something that it is not designed to do. You could try putting your request to the GRUB developers. 

Grub2 is working the way it was designed to but can be configured to work the way he/she wants. If I use the up or down keys I can halt countdown and suspend booting indefinitely. I believe the key is in those lines I highlighted. Commenting out GRUB_HIDDEN_TIMEOUT or putting the false from > GRUB_HIDDEN_TIMEOUT_QUIET=false in quotation marks might do the trick. Working with Grub customizer will prevent messing up stuff like that.

---

