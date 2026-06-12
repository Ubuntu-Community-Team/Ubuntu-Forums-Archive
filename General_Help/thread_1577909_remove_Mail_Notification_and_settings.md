---
title: "remove Mail Notification and settings"
date: 2010-09-19
forum: General Help
---

### Post by Poga on 2010-09-19
I've had Mail Notification installed for awhile, but was disappointed by the fact that it tries to check for e-mail before my computer can even establish an internet connection (and then never checks again), forcing me to manually start the program after every boot (an issue others have reported as well).

As a result, I removed the program via Ubuntu Software Center, and tried using cGmail (which I've used before, without issue), only to encounter [a bug]("https://bugs.launchpad.net/cgmail/+bug/503311").  I then uninstalled cGmail, and installed Mail Notification again.  However, as soon as I started Mail Notification, I noticed that it still had all of my preferences, including my previous e-mail account, saved.

How is this possible?  I tried removing it via Ubuntu Software Center, and then again with Synaptic---but still, if I reinstall it, the settings are all still there.  I want to completely remove Mail Notification, and all of its settings (even if I decide to eventually install it again), but now am confused as to how to do this.  Any suggestions?

---

### Post by cj13579 on 2010-09-19
Run the following command from a terminal:

```
sudo apt-get purge mail-notification
```

then try re-installing:

```
sudo apt-get install mail-notification
```

---

### Post by Poga on 2010-09-21
Thanks for the response.

I ran the purge command as you suggested, and then restarted my computer.  Mail Notification had been removed from my menus, and appeared to be uninstalled.  However, as soon as I reinstalled it, and opened the program, it remembered all of my previous settings and notified me of an e-mail in my previously attached e-mail account.

So, unfortunately, I'm still left a bit confused as to how to fix this.

---

### Post by Pug226 on 2010-12-05
I don't know if you are still interested, but the mail notification settings are in ~/.gnome2/mail-notification/mailboxes.xml. The passwords are stored in your keyring: System -> Preferences -> Passwords and Encryption Keys.

Note: Purging an application only deletes system-wide settings, not user specific settings.

---

