---
title: "Ubuntu won't boot, keeps reloading"
date: 2010-05-30
forum: General Help
---

### Post by JacquesKik on 2010-05-30
Hello, just yesterday I switched from windows to ubuntu, and I really enjoyed it.
Tonight, however, after installing and uninstalling a lot of addons, I rebooted it. To my surprise, the welcome screen just keeps reloading after I enter my pass.

I did some searching, now when I press ctrl+alt+f7, here's what I get:

[...] fsck from util-linux-ng 2.17.2
udevd[401]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/40-usrp.rules:1

udevd[401]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent  device, in /etc/udev/rules.d/40-usrp.rules:1

/dev/sda5: clean, 233213/567840 files, 1750400/2269173 blocks
 * Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable" usr.bin.firefox

* Setting sensors limits
SpamAssassin Mail Filter Daemon: disabled, see /etc/default/spamassassin
* gammu-smsd not yet configured, please edit /etc/gammu-smsdrc
* Not starting internet superserver: no services enabled.
* Starting Postfix Mail Transport Agent postfix


I should note that I still have Windows 7 running on the machine on a different partition, and that this is a 64bit Toshiba A500.

---

### Post by bakegoodz on 2010-05-30
The console messages don't give any clues. It seems you uninstalled something that Xwindows/Gnome needs to startup. On the console type login and type:
sudo aptitude install ubuntu-desktop 
that should restore all the files you removed Take a little more care in removing packages in the future

---

### Post by wilee-nilee on 2010-05-30
Since it is a fresh install and all it seems is there is a customized install, you might just consider deleting it with gparted or overwriting it with a fresh install, and maybe ask for some help when removing stuff.

I suggest this as a reinstall would be your fastest fix and allow you to get back to a working system. 

This may not fit with what you want so follow your own needs, but this sort of description with only a log file that is at best really not much information, will not get much help unless somebody really cares.

If you can list what you installed and removed it might be helpful, I don't like to see people chuck a OS but it is a borked fresh install.

---

### Post by JacquesKik on 2010-05-31
Thanks!
I did that command and it works now...

Well I did a lot of installing/uninstalling to try out applications.... but I remember removing Evolution (Thunderbird is a lot better) and Ubuntu One (useless for me).... could that have caused it ?

---

### Post by wilee-nilee on 2010-05-31
> **JacquesKik said:**
> Thanks!
I did that command and it works now...

Well I did a lot of installing/uninstalling to try out applications.... but I remember removing Evolution (Thunderbird is a lot better) and Ubuntu One (useless for me).... could that have caused it ?

That is great that the install the desktop got you back up. You want to really only remove stuff through synaptic, in lucid you can remove the basic evolution package but other parts of it are attached to the desktop. If you use synaptic it will tell you what else is being marked for removal. Stay away from the ubuntu software center, it doesn't inform you and really in my opinion shouldn't even be in the computer, but that's my personal preference.

Once you know what can be removed without losing important programs then the command line or even the software center can be used.

---

