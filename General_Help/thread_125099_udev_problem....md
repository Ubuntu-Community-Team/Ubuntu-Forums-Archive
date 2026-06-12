---
title: "udev problem..."
date: 2006-02-03
forum: General Help
---

### Post by vyruss on 2006-02-03
I've been using **udev** 0.70 or something along with hotplug, and it's worked perfectly fine until now. When I decided to go back to Breezy's (0.60) udev, all hell broke loose. When booting, the system totally hangs at "**Creating initial device nodes...**".

When I bypass it by pressing Ctrl+C the instant I see it, the system boots "normally" but cdroms aren't automounted anymore. I also find stuff like this in my **/var/log/syslog**:

```
Feb  3 07:57:23 gremlin usbmount[17338]: cannnot execute /sbin/udev_volume_id
```I'm now using **only Breezy's default packages** (udev, hotplug, initscripts, makedev, hal, hal-device-manager, hwdb-client, usbmount, initramfs-tools, kernel etc.)!

What's going on here, and more importantly, what can I do?

Many thanks!

---

### Post by vyruss on 2006-02-03
Sorry to bump like this, but this is a real problem for me and help would be greatly appreciated :(

---

### Post by dcstar on 2006-02-03
[QUOTE=vyruss]Sorry to bump like this, but this is a real problem for me and help would be greatly appreciated :([/QUOTE]
You have downgraded a software module, unless this software specifically said you could do this downgrade, you have probably now have an incompatible udev configuration, which is why it no longer works.

I would recommend a reinstall of Ubuntu.

---

### Post by vyruss on 2006-02-04
[QUOTE=dcstar]You have downgraded a software module, unless this software specifically said you could do this downgrade, you have probably now have an incompatible udev configuration, which is why it no longer works.

I would recommend a reinstall of Ubuntu.[/QUOTE]

What you mean is that moving from 0.60 -> 0.70 works and 0.70 -> 0.60 breaks things? 

I'd rather avoid "the windows way" and not reinstall... there has to be somebody around here who can tell me how to set up my udev! What puzzles me is that even if I totally remove udev (along with its configuration) and I reinstall it, it still refuses to work properly.

---

### Post by dcstar on 2006-02-04
[QUOTE=vyruss]What you mean is that moving from 0.60 -> 0.70 works and 0.70 -> 0.60 breaks things?
......[/QUOTE]
Software writers can plan for things to Upgrade, they rarely plan for things to Downgrade.

udev is probably using configuration information created by multiple items in your system when the system was installed (and possibly changed when 0.70 was installed), and it could take a long time to identify each one and try and recreate them.

This is the risk you take when hacking around with uncertified stuff.

---

