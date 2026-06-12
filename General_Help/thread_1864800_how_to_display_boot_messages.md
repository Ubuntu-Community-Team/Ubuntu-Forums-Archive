---
title: "how to display boot messages?"
date: 2011-10-19
forum: General Help
---

### Post by 3.14.TR on 2011-10-19
hi,
i'd like to display some text messages about the booting process during the booting itself. I tried to delte " quiet splash" from grub config, and than to update grup by $update-grub, or even xdiagnose, but only thing that changed after reboot wat that for a second, just before displaying the loginscreen, some messages appeared.
I'd prefer to display them as soon as possible, i.e. when the network is setting up, i'd like to see it etc.

I run xubuntu 11.04 on very old notebook, but i guess this problem is not about hardware

can you help, thanks

---

### Post by gsmanners on 2011-10-19
Since the advent of plymouth, you get framebuffered whether you want it or not (unless you remove plymouth, of course). If you want to know what the kernel is doing you can look at /var/log/dmesg (or just type dmesg in a terminal).

---

### Post by CharlesA on 2011-10-19
/var/log/bootlog will tell you a bit about the boot process if I remember right.

---

### Post by 3.14.TR on 2011-10-19
thanks, but I'd like to print it on the screen in the process of booting, just to know what part takes the lengest time etc, btw the notebook is really old and booting takes about 3minutes, and since only blackscreen appears, sometimes it may claim to be frozen etc, this could solve it...

---

### Post by CharlesA on 2011-10-19
Look into bootchart, it'll give you a chart of what takes the longest to load.

It's just an apt-get away.

---

### Post by 3.14.TR on 2011-10-19
ok, i guess its impossible to display it through the booting, no problem,

thank you guyes ;)

---

