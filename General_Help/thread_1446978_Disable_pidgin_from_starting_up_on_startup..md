---
title: "Disable pidgin from starting up on startup."
date: 2010-04-04
forum: General Help
---

### Post by HHx66 on 2010-04-04
Pidgin auto starts with the computer, I've closed out of it and killed the process and restarted to make sure it wasn't saving the session, it still starts, theres no option in any of the settings for pidgin to turn it off, is there a way to?

---

### Post by zanetu on 2010-04-04
Is there an entry for pidgin in "system settings" -> "advanced" -> "autostart"? If yes, disable or remove it.

---

### Post by HHx66 on 2010-04-14
Sorry about the late reply, I don't get a chance to get online much. And no, there isn't an entry there. So I don't know where its starting from, thanks in advance for any help. And very sorry about the late reply.

---

### Post by drs305 on 2010-04-14
This may clear the settings, even though you don't have it selected in the 'autostart' section.

Close out all your apps. You could try to be certain that Pidgin isn't running with:

```
killall pidgin  # Make sure pidgin isn't running
ps -u *yourusername*  # Check running processes.

```
Then System, Preferences, Startup Applications. In the Options tab, click the "Remember Currently Running Applications" (of which there should be none) and tick the "Automatically remember running applications when logging out". 

Reboot the computer, return to the Startup Programs tab, and untick "Automatically remember running applications when logging out". 

This was a technique I used a while back to kill a stubborn Pidgin that would always start on boot. It may still work.

---

