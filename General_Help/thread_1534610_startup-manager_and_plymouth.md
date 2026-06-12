---
title: "startup-manager and plymouth"
date: 2010-07-19
forum: General Help
---

### Post by zamarax on 2010-07-19
I wasn't able to find my exact issue anywhere else and apologies if has already been posted, 

I have ubuntu 10.04 64bit running on a Dell XPS m1530 with the nVidia 8600GT, when I first installed it everything was working fine however the plymouth resolution was very very low, so I used startup-manager to change my grub settings such as resolution and default boot, after doing this plymouth is broken, what I get know is a heavily distorted screen, it's black with lines of colours running through it, my question is did startup manager write something to the grub config that is causing this? how can it be fixed or undone?

Thanks!

---

### Post by anon.jdh on 2010-07-19
I read this great article last night, maybe it can help:

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by zamarax on 2010-07-19
thanks for that but it didn't help at all, if it's worth anything here is my grub.cfg file, 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=799 quiet"

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

---

### Post by zamarax on 2010-07-22
any other idea's?

---

### Post by zamarax on 2010-07-22
actually, I'm not exactly sure what caused it, but this article [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") fixed it.

---

### Post by anon.jdh on 2010-07-23
I'm adding that to my Plymouth arsenal documents.
Thanks.

---

### Post by H@rv3y on 2010-08-24
If you are using start-up manager, in the advanced tab change the resolution back to it's lowest. Restart and it will come back. It seems very sensitive to its resolution and if it will decide to display.
Using the etc/default/grub may work for you. I had start-up manager altered and followed directions on link, after restart, my system won't load past plymouth screen. Nightmare....

---

