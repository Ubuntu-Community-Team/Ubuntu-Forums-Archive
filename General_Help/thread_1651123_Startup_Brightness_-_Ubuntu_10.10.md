---
title: "Startup Brightness - Ubuntu 10.10"
date: 2010-12-22
forum: General Help
---

### Post by insane9 on 2010-12-22
Hi all,

just joined as i've got a problem and i don't know the fix for it (if there is one?).

I have an Asus X5DIJ laptop and i'm dual booting Win7 Home Premium & Ubuntu 10.10. 

When i boot into Ubuntu, my default brightness is on high. How to i set the default brightness so when i boot up, it's the same as it was when i last shut down?

many thanks

---

### Post by insane9 on 2010-12-22
Oops, my fault. I should have searched some more;

found this if anyone has the same issue:


Open gconf-editor and go to:

apps > gnome-power-manager > backlight

and change the setting there.

---

### Post by bdoe on 2010-12-22
I don't know if there's any way to have Ubuntu restore the last set screen brightness; I think it always reverts to default on boot-up. However, you can change your default brightness by setting it in your Power Management settings (System -> Preferences -> Power Management).

---

### Post by insane9 on 2010-12-22
> **bdoe said:**
> I don't know if there's any way to have Ubuntu restore the last set screen brightness; I think it always reverts to default on boot-up. However, you can change your default brightness by setting it in your Power Management settings (System -> Preferences -> Power Management).

thanks i'll play about with those settings. There is an option to 'set default' in Power Management, i'll give that a shot :-)

---

### Post by insane9 on 2010-12-22
got it working, i think it was a combination of both. Set the brightness to 0 and made default.

Rebooted and it's now as dim / as bright as i want.

Thanks for the help

---

