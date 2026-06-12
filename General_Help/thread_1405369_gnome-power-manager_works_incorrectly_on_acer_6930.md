---
title: "gnome-power-manager works incorrectly on acer 6930"
date: 2010-02-12
forum: General Help
---

### Post by bartlomiejp on 2010-02-12
Hi,
Laptop Acer Aspire 6930, Ubuntu 9.10 (Mint8).

When I switch my laptop on when it runs from a battery, gnome-power-manager shows that it works from AC. It is enough if I really plug AC in and unplug it again, than g-p-m knows it works on a battery...
It is frustrating when I want to use the laptop on the go, it doesn't know when battery is going to die.

Please help guys...

---

### Post by Harix on 2010-02-14
Same laptop, same problem, 9.10 karmic. Gnome power manager 2.28.1
No battery tab in preferences.
When I start the laptop without AC present, no indication and after 1 hour the laptop goes death instandly without any warning....

---

### Post by bartlomiejp on 2010-02-14
Ok.
I found this:
[http://www.mail-archive.com/devkit-devel@lists.freedesktop.org/msg00492.html]("http://www.mail-archive.com/devkit-devel@lists.freedesktop.org/msg00492.html")

gnome-power-manager is not the reason. It is devkit-power, it doesn't detect a battery on startup.

If you type this in the console:

> cat /proc/acpi/battery/BAT1/state

It will make devkit-power "see" that you are on the battery, and gnome-power-manager will give you correct information.

You can add:
> cat /proc/acpi/battery/BAT1/state
to your startup and system will be able to detect that you're on the battery.

---

### Post by Teh H4rRy on 2011-01-23
Thank you! I was having the exact same issue, I have had my laptop randomly shut down as i didnt know it was low on battery. Thanks for posting the fix.

---

