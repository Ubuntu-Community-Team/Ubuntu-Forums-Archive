---
title: "grub: Minimal Bash"
date: 2010-02-23
forum: General Help
---

### Post by 110686 on 2010-02-23
Hello,

When I tried to turn the grub boot menu off (I have Windows 7 and Ubuntu 9.10 installed via wubi and 2 boot menus were a bit annoying) things went wrong. I set the time from 10 to 0 in the config file.
When I now turn on my laptop and select Ubuntu, it loads grub and then shows me a message about a minimal bash line.:(

Can somebody solve this problem?

---

### Post by dabl on 2010-02-23
> **110686 said:**
> 

Can somebody solve this problem?

It should be possible to boot a Live CD, and then open the config file that you changed and edit it back to the way it was.

---

### Post by 110686 on 2010-02-23
I'll try re-changing the file by booting with a live cd.

---

### Post by 110686 on 2010-02-23
When I boot from a live CD that I've just burnt it seems like the file is OK.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
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
```I thought I changed the value behind GRUB_TIMEOUT. It seems to be OK here. This is the command I ran:

```
ubuntu@ubuntu:~$ gksu gedit /boot/grub/menu.lst
```When I then run the grub update command it says:

```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```Maybe this is just the file on the live cd, and not the one on my harddrive.:confused:

---

### Post by 110686 on 2010-03-03
Allright, I simply reinstalled from the wubi file, because that appeared to be (and was) the easiest way.

Now everything is running ([almost]("http://ubuntuforums.org/showthread.php?t=1413505")) smoothly again!

---

### Post by meierfra. on 2010-03-04
It's too late to prevent the reinstall, but you still should have a look at this link to prevent  this in the future:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by 110686 on 2010-03-05
This might be helpfull although I didn't try it because it was already fixed. Thanks anyway!

---

### Post by 110686 on 2010-03-08
After we -the grub command line and I- unfortunatly met again (this time it wasn't even my own fault, I just installed some updates), I can now confirm the solution described above indeed works!

---

