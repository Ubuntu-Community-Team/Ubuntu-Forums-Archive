---
title: "Ubuntu freezes up"
date: 2009-08-13
forum: General Help
---

### Post by Drjim on 2009-08-13
In general, I enjoy ubuntu. I'm running it in a separate partition on my hard drive so I can switch back and forth between ubuntu and windows. One of the things I was looking forward to was that Linux OS is supposed to be cleaner and free of many of the glitches in windows.

I've been upset to find that ubuntu will sometimes freeze up. Totally. The mouse and keyboard are unresponsive. I can't exit a program or even restart ubuntu. The only thing that works is to hold down the power button on my computer until the machine turns off and then restart everything.

This seems more likely to happen if I leave my computer unattended for awhile and it goes into suspend mode (but not always). I often (but not always) get a message that "your computer failed to go into suspend mode". Is there any equivalent to "ctrl-alt-del" to exit frozen programs like in windows? Any other suggestions?

Thanks,

Jim

---

### Post by NH2G on 2009-08-13
Every once in a while, this happens to me too.

---

### Post by P4man on 2009-08-13
What version of ubuntu and what kernel are you using (you can find out the kernel by typing:

```
uname -r
```

in a terminal window. 

I'm seeing a lot of lockups posted here, and having it myself on one machine with ubuntu jaunty and the latest 2.6.28-14 kernel. It might be worth trying to boot using an older kernel (in the grub menu you will probably have that option).

As for the failure to go in to suspend mode.. assuming you have jaunty, perhaps this is worth trying and reporting:

[https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)

---

### Post by zkriesse on 2009-08-13
Sad to say no. There is not to my knowledge a 'ctrl/alt/delete/ equivalent in Ubuntu or even in Linux.

---

### Post by P4man on 2009-08-13
nothing helps if you have a kernel panic (frozen mouse and keyboard, blinking keyboard leds). But there are some equivalents. 

control+alt+backspace restarts X, if you enable it again:

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

If you like, you can assign control+alt+delete to system monitor with gconftool, or type this in a terminal:```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
```

Lastly, you can right click on a gnome panel and add the "force quit" applet, which is a convenient way to close misbehaving apps.

But again, none of that will help if you are having kernel panics.

---

### Post by Drjim on 2009-08-14
Lastly, you can right click on a gnome panel and add the "force quit" applet, which is a convenient way to close misbehaving apps.

But again, none of that will help if you are having kernel panics.[/QUOTE]




What's a gnome panel?

Jim

---

### Post by P4man on 2009-08-14
> **Drjim said:**
> 

What's a gnome panel?

Jim

the 2 bars you get on top and bottom of the screen on a default gnome desktop. They are called "panels"

---

