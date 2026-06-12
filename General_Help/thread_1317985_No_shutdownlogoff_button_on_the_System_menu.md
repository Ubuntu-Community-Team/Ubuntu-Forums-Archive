---
title: "No shutdown/logoff button on the System menu"
date: 2009-11-07
forum: General Help
---

### Post by blueshiftoverwatch on 2009-11-07
On Ubuntu 9.04 there was a shutdown/logout button in System menu. It would bring up a small window in the center of the screen asking if you wanted to log off, switch user, restart, shut down, etc. Ubuntu 9.10 seems to have gotten rid of this.

How can I add that particular menu option back to the System menu so that I can remove the logoff/shutdown button on my taskbar which comes by default?

I went to the "main menu" menu editor under Preferences but didn't see an option to add that button. Is it hidden somewhere or would I have to add a "new item" and enter in the command to enable that button? If yes, what is the command?

---

### Post by pastalavista on 2009-11-07
I missed that too. The "Fast User Switcher" is gone from the panel too. I added the applet "Indicator Applet Session" to the panel which has the same funtion. Right-click the panel and select "Add to panel".

---

### Post by 101011010010 on 2009-11-07
Hello there .
I'm not sure, but I think you're looking for the "shut down" applet. It's at the bottom of the "add to panel" list. So is "user switcher".
I hope this helps.

---

### Post by blueshiftoverwatch on 2009-11-07
I'm aware that I can add those applets to the panel. But I want to be able to go to do that from within the System drop down menu. Since a picture is worth a thousand words Something like [this]("http://decoding.files.wordpress.com/2007/04/shutdown.jpg") is what I want to come up when I go to shutdown/restart/log off/etc. Only have it be accessible from within the System menu and not directly from the taskbar it's self. Basically going back to the way Ubuntu would let you log off in previous releases.

---

### Post by blueshiftoverwatch on 2009-11-10
Bump.

---

### Post by williamreisinger on 2009-11-11
Right clicking doesn't produce "add to panel".  It does produce "remove from panel".  ???

---

### Post by lswb on 2009-11-11
I don't know about 9.10 but in 9.04, the shutdown and logout menu items do not appear in a default installation until the Fast User Switcher Annoyance is removed from the panel, then they are automatically added.

If you need to manually add them to the menu, in 9.04 they could be called with the "gnome-session-save" command. I guess it is the same in 9.10. See the man page to be sure of the correct options to use. In 9.04 "gnome-session-save --logout-dialog" and "gnome-session-save --shutdown-dialog" bring up the dialogs. There are also options for immediate logout and shutdown (without any dialog box)

---

### Post by blueshiftoverwatch on 2009-11-11
> **lswb said:**
> I don't know about 9.10 but in 9.04, the shutdown and logout menu items do not appear in a default installation until the Fast User Switcher Annoyance is removed from the panel, then they are automatically added.

If you need to manually add them to the menu, in 9.04 they could be called with the "gnome-session-save" command. I guess it is the same in 9.10. See the man page to be sure of the correct options to use. In 9.04 "gnome-session-save --logout-dialog" and "gnome-session-save --shutdown-dialog" bring up the dialogs. There are also options for immediate logout and shutdown (without any dialog box)
That's neat, I just assumed that if I removed the logout applet from the panel that I wouldn't be able to log out using the until I re-added it to the panel or looked up the appropriate CLI commands.

---

