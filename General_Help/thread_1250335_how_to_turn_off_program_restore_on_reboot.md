---
title: "how to turn off program restore on reboot"
date: 2009-08-26
forum: General Help
---

### Post by sdwinder on 2009-08-26
I am having a problem with my current xubuntu installation, I am in a situation where I need to run firefox for a prolonged period of time on a machine. Sometimes the machine will freeze or need to be reset (power button) the problem with this is that everytime the machine is turned off while firefox is still running, when the machine comes back to desktop it tries to restore firefox, I need to turn this option off in linux. I know that it is not a firefox issue because I have turned off the crash restore option, so it must be something inside linux. I already have firefox set to launch on startup, so when it tries to launch it, since the OS is trying to restore it at the same time, I get the "firefox is already running" error. Ide like to know if there is a way to stop xubuntu from trying to restore firefox after a restart.

---

### Post by ScarySquirrel on 2010-04-23
XFCE-session-manager restores open programs on reboot. 
This help page discusses how to turn the ****er off: [http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfce4-session-settings]("http://www.xfce.org/documentation/4.2/manuals/xfce4-session#xfce4-session-settings")

Have fun with that.

---

### Post by oldfred on 2010-04-23
Firefox saves a lock files so it knows it is running. You may have to delete that on reboot with a startup script.

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

