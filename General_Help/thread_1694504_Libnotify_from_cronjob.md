---
title: "Libnotify from cronjob?"
date: 2011-02-24
forum: General Help
---

### Post by Flobbes on 2011-02-24
Is it possible to send a libnotify from a cronjob?

I'd like a notify message when my daily backup is done.
When I run my script from terminal everything is working fine, when (ana)cron runs it, it works as well but the notify is surpressed. My Guess was, that it happens because the jobs are run as root.

Nevertheless is it possible to get a notification message?

Thanks in advance.

---

### Post by gmargo on 2011-02-24
Cron jobs run with a very limited environment.  That environment does not include the DBUS_SESSION_BUS_ADDRESS variable that is required to send a notification.  Why not just use email?

Update: as pointed out below, the DISPLAY environment variable works too, and is clearly easier to use.

---

### Post by Flobbes on 2011-02-24
Would be ok as well, but I have no idea how to accomplish that.

---

### Post by Cheesehead on 2011-02-24
Use the notify-send command:
```
DISPLAY=:0.0 sudo -u USERNAME notify-send "Your Message Here"
```
(You need an appropriate username and message, of course)
Put that as the last line in your daily backup script.
The DISPLAY and sudo -u are to send the notification to your display instead of root's, and to avoid sending the notification as root.

---

### Post by Flobbes on 2011-02-25
Thanks a lot it worked perfectly!

---

