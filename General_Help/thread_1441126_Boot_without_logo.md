---
title: "Boot without logo"
date: 2010-03-28
forum: General Help
---

### Post by BobLand on 2010-03-28
I'd prefer to watch the boot loader do its thing.  I removed usplash but only see a very few commands.  What do I do to see every step/command?

Thanks,
bobland

---

### Post by MichealH on 2010-03-28
In the GRUB edit the boot option and remove --quiet-splash

---

### Post by efflandt on 2010-03-28
Do not edit grub.cfg, since that will be changed by kernel updates.  Edit /etc/default/grub (you have to be root so use **su gkedit** or **sudo nano**):

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Comment that out if you want to know what it looked like and copy it without quiet or splash:

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""

The GRUB_CMDLINE_LINUX="" line is for (recovery) grub menu entries

Then do **sudo update-grub**

---

### Post by BobLand on 2010-03-28
Thanks guys.  That did the trick.

I don't get a grub menu so the system is waiting out the time out period.  How would I see the menu?

Also, is there a way to change the screen resolution while in text mode?  It looks like I'm in a 640 mode.  I'd like to change to that 1280 or smaller.

Thanks again,
bobland

---

### Post by GeoMX on 2010-04-17
If you have only one OS installed, GRUB bypasses the menu, to force its appearance you can press [Shift] while GRUB is loading.

You can set GRUB resolution editing /etc/default/grub, just like you did when disabling the splash image, look for the GRUB_GFXMODE variable.

---

