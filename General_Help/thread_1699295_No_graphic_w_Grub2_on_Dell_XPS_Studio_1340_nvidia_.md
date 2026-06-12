---
title: "No graphic w/ Grub2 on Dell XPS Studio 1340 nvidia GeForce9400M"
date: 2011-03-03
forum: General Help
---

### Post by DougRS on 2011-03-03
I had installed the Ubuntu 10.04 with success. Everything worked fine. Then, I've upgraded to 10.10 Merkaat via apt-get and a lot of things stopped to work. After a lot of time spent and almost OK, I still have some issues not OK yet.

I use a Dell XPS Studio 1340 (laptop) nvidia GeForce9400M, 1280x800 resolution (max).

[LIST]
[*]Grub: the terminal, the splash (plymouth), X org, Gnome, all them are 1280x800x24 but the Grub screen itself. The Grub menu screen is showing 80x25 text (console). Between boot and this menu screen, it shows a pretty fast error (during about 80miliseconds) showing "error: no mods found..." so far I got read.
[*]The nvidia driver is 260.19.06 provided by apt-get. I've installed 260.19.36 direct from nvidia website, same results.
[*]Sometimes, when I close the lid (suspend) it suspends like a charm (1-3 seconds). But half of the times, it freezes/hangs and I lose all my tasks and I have to restart.
[/LIST]
My /etc/default/grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset splash video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"

#GRUB_TERMINAL=console

GRUB_GFXMODE=1280×800,1024×768,800×600,640×480,320×240
GRUB_GFXPAYLOAD_LINUX=1024x768x8

---

Any clue?

Any help is appreciated. Thank you,

Doug.

---

