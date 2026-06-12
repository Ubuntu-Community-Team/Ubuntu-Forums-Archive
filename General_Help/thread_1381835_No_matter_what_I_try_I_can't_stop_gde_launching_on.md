---
title: "No matter what I try I can't stop gde launching on startup"
date: 2010-01-15
forum: General Help
---

### Post by intermentals on 2010-01-15
Hi guys,

I'm running Ubuntu 9.10 (I installed server then installed the desktop packages)

I have tried "sudo update-rc.d -f gdm remove"

I have also tried creating an inittab file in /etc with the line id:3:initdefault

but neither work for me - any ideas?

---

### Post by intermentals on 2010-01-16
bump

---

### Post by sisco311 on 2010-01-16
9.10 uses Upstart. You can:

[list=i]

[*]append the linux line in Grub with the *text* kernel parameter:

edit the *GRUB_CMDLINE_LINUX_DEFAULT="quiet **text**"* line in /etc/default/grub then run: 
```
sudo update-grub
```

or
[*]edit /etc/X11/default-display-manager and comment out the */usr/sbin/gdm* line.

or
[*]rename the  /etc/init/gdm.conf file:
```
sudo mv /etc/init/gdm.conf /etc/init/gdm.conf.noexec
```

or
[*]edit the /etc/init/gdm.conf file and comment out the *start on* entry:
```
...
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

**#**start on (filesystem
**#**          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
**#**               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
**#**               or stopped udevtrigger))
stop on runlevel [016]

emits starting-dm
...

```

[/list]

---

### Post by intermentals on 2010-01-16
EDIT: sorry I refreshed the screen and it reposted

---

### Post by intermentals on 2010-01-16
ok thank you so much for taking the time to respond

having tried your suggested solutions however I am still stuck

the first one resulted in this error message: "/etc/default/grub: 9: text”: not found"

the next three all result in the system hanging on startup after the checking battery status message comes up with "done" - it wont proceed any further

---

### Post by sisco311 on 2010-01-16
> **intermentals said:**
> ok thank you so much for taking the time to respond

having tried your suggested solutions however I am still stuck

the first one resulted in this error message: "/etc/default/grub: 9: text&#8221;: not found"

the next three all result in the system hanging on startup after the checking battery status message comes up with "done" - it wont proceed any further

Please post the content of the /etc/default/grub file.

---

### Post by intermentals on 2010-01-17
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet text&#8221;
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

---

### Post by intermentals on 2010-01-17
having posted that I can see the error myself, and having corrected the quotation marks it now works - thank you

---

