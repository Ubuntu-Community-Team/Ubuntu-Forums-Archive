---
title: "Writing log files with a shell script"
date: 2011-02-06
forum: General Help
---

### Post by whatthefunk on 2011-02-06
I want to perform an action with a shell script and then log the event in a file in /var/log.  However, I keep getting permission denied error messages.  How can I do this?
Thanks

---

### Post by Old *ix Geek on 2011-02-06
> **whatthefunk said:**
> I want to perform an action with a shell script and then log the event in a file in /var/log. However, I keep getting permission denied error messages.  How can I do this?The permissions on /var/log are preventing you from writing to it. Is the script something you're going to run manually or will it be set up to run automatically [via cron, etc.]?

---

### Post by whatthefunk on 2011-02-06
Ill be running it manually.

---

### Post by whatthefunk on 2011-02-06
I got something to work.  I made a new log file and changed the permissions to 666.  Not the best solution I think, but it works for now.

---

### Post by anglican on 2011-02-07
> **whatthefunk said:**
> I want to perform an action with a shell script and then log the event in a file in /var/log.  However, I keep getting permission denied error messages.  How can I do this?
ThanksI'd use logger to do this e.g.
```
logger -i "This is a test message"
```will cause the message and the process id of logger to be written at the end of /var/log/messages. See the logger man page for further options. It will run as a standard user (no need for sudo).

H

---

### Post by geirha on 2011-02-07
> **whatthefunk said:**
> I got something to work.  I made a new log file and changed the permissions to 666.  Not the best solution I think, but it works for now.

That's a bad idea. Instead, make it 644 or 664, and chown it to the user that needs to write to it.

---

