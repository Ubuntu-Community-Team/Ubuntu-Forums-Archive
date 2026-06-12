---
title: "How to select other OS with 11.10"
date: 2011-12-01
forum: General Help
---

### Post by cearlp on 2011-12-01
I think this is probably a simple problem, but here it is.
I installed 10.10 onto a empty disk and it boots automatically when the computer is turned on, i.e. there is no screen to allow the selection of recovery mode or  memtest86 or previous releases.
In all my other installations or upgrades grub gives me the choice to make a selection.
I installed another OS along side of 10.10 but when I restart the box it still boots immediately to 10.10.
Is there a key I need to hold down while booting or do I need to do something with grub or what?

---

### Post by utnubuuser on 2011-12-01
Press ESC within first 3 seconds of booting... or,


Change parameters in /etc/default/grub

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=" vga=792 splash

comment out GRUB_HIDDEN_TIMEOUT
and change the HIDDEN_TIMEOUT_QUIET to false, then run sudo update-grub

---

### Post by cearlp on 2011-12-01
Thanks utnubuuser. Things look good to me now.

---

