---
title: "Problems in grub2"
date: 2011-03-24
forum: General Help
---

### Post by Veoden on 2011-03-24
I have a installation with 2 Hds.

/dev/sda1 mount in /media
/dev/sbd1 mount in /
/dev/sdb2 mount as swap

The sda crashed, so i lost the grub.
I change the sdb to sda now i have two partition.
sda1 as / and sda2 as swap
I boot with Live CD mount sda1 in mnt and install grub in sda.

Everything works fine except the grub is not respecting the timeout configuration.
I put in /etc/default/grub GRUB_TIMEOUT=2 and update grub, but when i restart the system act as the GRUB_TIMEOUT=-1

I look at /boot/grub/grub.cfg and find this code:
```

if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi

```

---

### Post by Bucky Ball on 2011-03-24
Not sure if you are using grub legacy or grub2 but looks like you might be using the latter. Change settings in:

/etc/default/grub

Then:

sudo update-grub

... in a terminal.

Without the 'sudo update-grub' your changes will make no diff.

Leave .cfg file alone. ;)

---

### Post by Veoden on 2011-03-24
> **Bucky Ball said:**
> Not sure if you are using grub legacy or grub2 but looks like you might be using the latter. Change settings in:

/etc/default/grub

Then:

sudo update-grub

... in a terminal.

Without the 'sudo update-grub' your changes will make no diff.

Leave .cfg file alone. ;)

I am using grub2 and all modifications is in /etc/default/grub and i execute sudo update-grub, I just show the .cfg to show that the grub apply the modifications that i made, but still have the problem.

---

### Post by Bucky Ball on 2011-03-24
Try hitting escape or shift when you boot the machine (this should take you to the grub menu but the method has changed so could be either).

---

### Post by andrewthomas on 2011-03-24
Post your /etc/default/grub

```
cat /etc/default/grub
```

---

### Post by Veoden on 2011-03-24
> **andrewthomas said:**
> Post your /etc/default/grub

```
cat /etc/default/grub
```

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xbmc=autostart,nodiskmount loglevel=0"
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

# Defaults from XBMC Installation
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xbmc=autostart,nodiskmount loglevel=0 video=vesafb"
GRUB_GFXMODE="800x600"
GRUB_GFXPAYLOAD_LINUX="800x600"

```

---

