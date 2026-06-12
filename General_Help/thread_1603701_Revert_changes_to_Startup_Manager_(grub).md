---
title: "Revert changes to Startup Manager (grub)"
date: 2010-10-23
forum: General Help
---

### Post by kalos on 2010-10-23
I just installed Ubuntu 10.10 and I installed and messed around with [startupmanager]("https://help.ubuntu.com/community/StartUpManager"). Now I get status text when I startup, shutdown, and resume from suspend.

I have "show text during boot" disabled. And I tried turning "show boot splash" on.

How can I get the default behaviour?

---

### Post by sikander3786 on 2010-10-23
Not sure about StartUp Manager, but it will be easy to find out if you post the text from /etc/default/grub.

```
gedit /etc/default/grub
```

---

### Post by kalos on 2010-10-23
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=771"

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

```

---

### Post by sikander3786 on 2010-10-23
I think this line is causing problems.

```
GRUB_CMDLINE_LINUX=" splash quiet vga=771"
```

Which graphics card have you got? Is it really necessary to add vga=771?

If it is not needed, just edit /etc/default/grub and delete "splash quiet vga=771 "from the above mentioned line so it looks like,

```
GRUB_CMDLINE_LINUX=""
```

Now run

```
sudo update-grub
```

Note: If you are unsure, please post details about your graphics card prior to editing or you might end with a blank screen at boot.

---

### Post by kalos on 2010-10-23
Thanks! That worked.

Messing around with the options again, it looks like changing the resolution option in startupmanager added the vga=xxx option, but startupmanager doesn't have any way of removing it, so I had to resort to editing manually. I filed a [feature request]("https://bugs.launchpad.net/startup-manager/+bug/665682").

Thanks again sikander.

---

### Post by sikander3786 on 2010-10-23
You are Welcome :-)

Just an explanation, GRUB_CMDLINE_LINUX="" is intended for adding custom commands at the end of kernel line during boot. Resolution is controlled by GRUB_GFXMODE instead. A wealth of information here,

[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)

---

