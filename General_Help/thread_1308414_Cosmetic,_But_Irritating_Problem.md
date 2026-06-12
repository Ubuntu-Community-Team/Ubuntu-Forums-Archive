---
title: "Cosmetic, But Irritating Problem"
date: 2009-10-31
forum: General Help
---

### Post by moore.bryan on 2009-10-31
Okay... after doing what I always do and tinker with every feasible setting, my Karmic has SNAFU-ed me.

I've lost the "throbbing" Ubuntu logo after my grub2 list and I get text. I'm not sure what I've screwed-up and/or changed, but I'd like to not see the text. My /etc/default/grub is below... Help!!!
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
GRUB_CMDLINE_LINUX="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

---

### Post by moore.bryan on 2009-11-02
Should've known... a simple "sudo update-alternatives --config usplash-artwork.so" and choosing the appropriate usplash fixed it. Lord Ockham was right.

---

