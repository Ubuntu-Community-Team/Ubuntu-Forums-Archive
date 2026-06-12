---
title: "Ubuntu Stuck At &quot;checking state of battery&quot; screen. URGENT."
date: 2010-11-13
forum: General Help
---

### Post by hxcjonnysniper on 2010-11-13
i am running ubuntu 10.10
i tried installing nvidia drivers earlier.
it said something about configuring X server as root.
so i restarted my laptop and now i get stuck at the screen that says "checking state of battery"
i know i can press ctrl alt F2.
and i tried a few commands but nothing works.
someone please help me get my computer back?
:(

---

### Post by Monotoko on 2010-11-13
Why did you restart the laptop after it said "it said something about configuring X server as root."?

You should be able to boot into the recovery console from the startup menu (press Esc repeatedly after you turn your computer on if you do not see it)

From there you can repair the X server.

---

### Post by hxcjonnysniper on 2010-11-13
idk why i restarted it.
it says i wasn't root so i figured to reboot the system might solve it.
i did this in recovery mode
cd /etc/X11
cp xorg.conf xorg.conf.backup
Xorg -configure
cp /root/xorg.conf.new xorg.conf
reboot
still got nothing. im stuck on the same screen.
=/

---

### Post by Ancanus on 2010-11-13
What happens if you try to boot without a xorg.conf file?

---

### Post by popaclay on 2010-11-13
> **hxcjonnysniper said:**
> i am running ubuntu 10.10
i tried installing nvidia drivers earlier.
it said something about configuring X server as root.
so i restarted my laptop and now i get stuck at the screen that says "checking state of battery"
i know i can press ctrl alt F2.
and i tried a few commands but nothing works.
someone please help me get my computer back?
:(

funny the last week or so when booting it stops and says the battery is low and I have to restore defaults motherboard settings. However I am running 10.04.

---

