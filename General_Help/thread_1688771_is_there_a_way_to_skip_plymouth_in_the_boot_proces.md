---
title: "is there a way to skip plymouth in the boot process?"
date: 2011-02-15
forum: General Help
---

### Post by maddbaron on 2011-02-15
Tryin to trouble shoot my machine. Is there a way I can skip the plymouth/user login part of the boot process?] and go from grub then those command line sentences to desktop directly?

---

### Post by matt-fender on 2011-02-16
I installed bum ( Boot-Up Manager )

```
sudo apt-get install bum
```

once installed it can be run from System > Administration

Using this program I have disabled Plymouth, and a few other bits and bobs like printing and blue-tooth ( things I'll never use )

I then proceeded to System > Administration > Login Screen

Once opened. "Unlock" the settings with your password

The rest should be pretty self explanatory :p

---

### Post by mc4man on 2011-02-16
edit your /etc/default/grub - remove the quiet splash from the GRUB_CMDLINE_LINUX_DEFAULT= line
Ex. mine
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

blah, blah
run sudo update-grub after editing

---

### Post by maddbaron on 2011-02-16
thanks for the help both you of, very beneficial stuff and the bum application showed me things starting that I didn't know about.

---

### Post by psusi on 2011-02-16
Plymouth is a required part of the system and can not be disabled without causing breakage.  It multiplexes the console so that other processes like the disk check or disk encryption password prompt can get your attention if they need to.

---

