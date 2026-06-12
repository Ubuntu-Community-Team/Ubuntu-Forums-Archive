---
title: "Booting 11.10"
date: 2012-01-07
forum: General Help
---

### Post by creiss on 2012-01-07
Hey all,

For some odd reason my Grub menu pops up on boot.
Single OS layout, Ubuntu 11.10 on notebook.

I want it to be ultra silent and "just" boot Ubuntu.

How would I go about fixing this?

Thanks all for your effort & advice!
-Chris

---

### Post by creiss on 2012-01-09
Shameless bump. *blush*

---

### Post by Derek Karpinski on 2012-01-09
```
gksudo gedit /etc/default/grub
```Find the line with:

#GRUB_HIDDEN_TIMEOUT=0

And change it to:

GRUB_HIDDEN_TIMEOUT=0

Save the file.

```
sudo update-grub
```

Reboot.

source: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by creiss on 2012-01-09
Thanks for your reply,

stuff already is in place. Here is an unmodified from my system:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

