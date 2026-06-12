---
title: "multiple problems after update"
date: 2009-11-28
forum: General Help
---

### Post by aftermgates on 2009-11-28
After installing a large amount of updates last night, I have run into several problems:
1. Before the login screen comes up I get the message:
"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
2. When the login screen comes up I get "the configuration defaults for gnome power manager have not been installed correctly"

After logging into Gnome I get the first message again and the login screen comes back up.
Logging into failsafe gnome gives the second message and a black screen with a working mouse; not able to do anything but hit the power button and reboot.

All help is, of course, greatly appreciated.

---

### Post by DapperMe17 on 2009-11-28
+1 for the first problem....won't boot.

My suggestion is to go back to 8.04, at least for a while. It's nearly flawless & there will continue to be many teething problems short-term for Karmic. 

I've been running Karmic for a couple of weeks & it performs quicker for me, than Hardy. 

However, I've had nothing but trouble with the new Grub2.

You could try booting from the LiveCD & doing a fsck -l.

---

### Post by iponeverything on 2009-11-28
Try the solution posted in:

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269244](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269244)

---

