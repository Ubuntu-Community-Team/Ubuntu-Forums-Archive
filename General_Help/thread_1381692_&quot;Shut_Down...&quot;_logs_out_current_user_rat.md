---
title: "&quot;Shut Down...&quot; logs out current user rather than shutdown"
date: 2010-01-15
forum: General Help
---

### Post by nealio on 2010-01-15
I've done a fresh install of Karmic 9.10. I'm running on an ASUS laptop (Core 2 Duo, 2GB RAM, NVIDIA GeForce 7300).
 **Problem:**
When shutting down via the In Indicator applet (i.e. top right menu where one of the options is "Shut Down..."), the system seems to log out the user instead. Then at the user login screen, I have to select "shut down" from there before the laptop powers off.
 

I've also discovered that from the GNOME desktop if I open a terminal and do "sudo shutdown -h now", the system powers off as expected without any further action. Seems like a permissions problem even though the account is the administrator and is the account used for sudo actions.


Any ideas greatly appreciated as this is very annoying since the upgrade!

---

### Post by hariks0 on 2010-01-15
If you are using compiz, the link at my signature may help you. Set the value of some command to ```

gnome-session-save --shutdown-dialog
``` The button binding I use is Ctrl+Button3.

---

