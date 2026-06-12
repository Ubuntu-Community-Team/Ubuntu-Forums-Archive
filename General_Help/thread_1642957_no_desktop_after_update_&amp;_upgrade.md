---
title: "no desktop after update &amp; upgrade"
date: 2010-12-11
forum: General Help
---

### Post by joselitux on 2010-12-11
Hi all

After my latest maverick apt-get update & upgrade, a new kernel is installed (2.6.35-24-generic). Everything seems to be fine but if I choose it, no desktop is loaded. It ends with a console and a login request. I can't boot-up the gnome desktop unless I choose the former kernel (2.6.35-23-generic).


Any suggestion?

---

### Post by karthick87 on 2010-12-11
Give you username and password in that console..And type the following command

```
startx
```or

```
sudo /etc/init.d/gdm start
```

---

### Post by argedion on 2010-12-11
> After my latest maverick apt-get update & upgrade, a new kernel is installed (2.6.35-24-generic)

dont know if it is different with meerkat or not but I'm running lucid and my kernel is (2.6.35-26-generic) but I never had an update not start my x system so I'm not sure whats going on there. Karthick's way should allow you to log on and check for further updates

---

### Post by joselitux on 2010-12-11
starx gives a Fatal server error: "no screens found"

sudo /stc/init.d/gdm start gives me a long speech recommending to use other commands like "start gdm" or "service gdm start" none of them working

---

### Post by karthick87 on 2010-12-11
Have you tried,
```
start gdm
```
```
service gdm start
```

---

### Post by joselitux on 2010-12-11
yes, without success

---

### Post by karthick87 on 2010-12-11
Can you post the output of,
```

cat /etc/default/grub
```

---

### Post by joselitux on 2010-12-11
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
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
```

---

