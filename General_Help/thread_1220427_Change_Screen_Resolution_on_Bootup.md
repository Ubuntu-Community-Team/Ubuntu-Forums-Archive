---
title: "Change Screen Resolution on Bootup?"
date: 2009-07-22
forum: General Help
---

### Post by rmhartman on 2009-07-22
After upgrading the OS, it selected a new screen resolution my monitor can not display (I don't know why it changed those settings!)

Is there anything I can add after pressing 'e' on the boot up to select a screen resolution that my monitor is capable of displaying (1024x768) ?

---

### Post by fooman on 2009-07-22
reboot and when you get to the grub menu,  choose recovery mode....once there,  choose the "x fix" option.  then continue with boot and see if its any better.

if you get back to your desktop,  you will probably need to reinstall your video drivers.

hope that helps.

---

### Post by rmhartman on 2009-07-23
Ok, did that and I've been sitting here for the past 20 minutes looking at:
...
* Starting DHCP D-Bus daemon dhcdbd                   [ OK ]     
* Starting Hardware abstraction layer hald                  _

(the underscore at the end of the line is the cursor)

Got any other ideas?

---

### Post by rmhartman on 2009-07-23
Ok.  Went through recovery mode again, this time dropped into command line mode.

/etc/X11/xorg.conf seems to be a generic one rebuilt by the xfix option
there is an xorg.conf.{bunchanumbers} which seems to be a backup of the one present before the xfix attempt
renamed that one to xorg.conf
Section "Screen" states that the monitor is a "Dell E151FPp".  Dunno if that is correct, the model# on the monitor is behind the power cable ... but the subsection "Display" says
   Modes "1024x768" "800x600" "720x400" "640x480"
which does look correct.
I see nothing about color depth (probably not significant)
I see nothing about refresh rates
I do not see a display driver section
I see nothing about which mode actually will be used, although since max is 1024x768 it should be ok ... but if they're trying to run it at too high a refresh rate it wouldn't work.

where else should I be looking?

---

### Post by CatKiller on 2009-07-23
> **rmhartman said:**
> where else should I be looking?

/var/log/Xorg.0.log.

It may say which mode it's picked, and potentially why.

---

### Post by rmhartman on 2009-07-23
How about where should I look to configure the proper mode?

---

### Post by CatKiller on 2009-07-23
> **rmhartman said:**
> How about where should I look to configure the proper mode?

That probably depends on why the incorrect mode is being chosen.

---

