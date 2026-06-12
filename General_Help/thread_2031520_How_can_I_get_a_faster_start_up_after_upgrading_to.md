---
title: "How can I get a faster start up after upgrading to 12.04?"
date: 2012-07-22
forum: General Help
---

### Post by HunterDX77M on 2012-07-22
I upgraded to 12.04 recently but have noticed that start up times are now really long, much longer than they were in 11.10. My start up programs are all pretty much the same as they were in 11.10, so that's not the issue. Has anyone else experienced this and found a good fix for it? Thanks!

Specs:
Pentium Dual-core T4200 @ 2.00 GHZ
3.9 GB RAM
Mobile Intel 4 Series Express Chipset Family

Startup Time: ~40 seconds
Shutdown Time: ~3 seconds

---

### Post by PhantomTurtle on 2012-07-22
> **HunterDX77M said:**
> I upgraded to 12.04 recently but have noticed that start up times are now really long, much longer than they were in 11.10. My start up programs are all pretty much the same as they were in 11.10, so that's not the issue. Has anyone else experienced this and found a good fix for it? Thanks!

I haven't experienced this but maybe it could be Unity that's slow(maybe).

---

### Post by HunterDX77M on 2012-07-22
> **PhantomTurtle said:**
> I haven't experienced this but maybe it could be Unity that's slow(maybe).

But if it's Unity that's doing it, I would have noticed in 11.10 where I was also using Unity. I'm thinking its something else.

So far I tried using bum to see if I could get rid of some unneeded processes, but I have not seen any improvement in start up. (On the plus side, after using bum, my shutdown is like 3 seconds now).

How can I know what program/process is stalling while the system is booting up?

---

### Post by oldfred on 2012-07-22
How long is it taking to boot?

You can remove splash quiet and watch the drivers & processes as it boots. That same info is then in the log file dmesg. You can use log file viewer to review it. I use gnome panel so I think you just type log file viewer in Unity.

I look for a process that takes a long time or one that repeats & then fails.

---

### Post by sudodus on 2012-07-22
Please post the specs of your computer: CPU, RAM, graphics card or chip!

This makes it easier to guess and suggest what to do. Maybe you should use a desktop environment with a lighter foot-print. Maybe you need another graphics driver ...

---

### Post by HunterDX77M on 2012-07-22
> **oldfred said:**
> How long is it taking to boot?

You can remove splash quiet and watch the drivers & processes as it boots. That same info is then in the log file dmesg. You can use log file viewer to review it. I use gnome panel so I think you just type log file viewer in Unity.

I look for a process that takes a long time or one that repeats & then fails.

I don't see dmesg when I open up log file viewer. How can I disable (and later re-enable) splash quiet?

---

### Post by sudodus on 2012-07-22
> **HunterDX77M said:**
> I don't see dmesg when I open up log file viewer. How can I disable (and later re-enable) splash quiet?
Either do it at each boot editing the command line underneath each choice in the grub menu: e to edit ...

or edit the file ***/etc/default/grub***: the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and then run ```
sudo update-grub
``` followed by ```
sudo reboot
```

---

### Post by oldfred on 2012-07-22
You can also edit it each time you boot. At grub menu (use shift to get it from BIOS is not normally shown).

Press e - edit on grub entry and edit out the quiet splash. Control-x to boot.

If Log file viewer does not show it as default, you have to load it. File open, and log files are in var, log.

---

