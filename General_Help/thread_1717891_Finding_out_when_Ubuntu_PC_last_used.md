---
title: "Finding out when Ubuntu PC last used"
date: 2011-03-30
forum: General Help
---

### Post by welshmike on 2011-03-30
Is there a log that will tell me when my Ubuntu system was last used please?

---

### Post by Karlchen on 2011-03-30
Hello, welshmike.

Just have a look at the logfile /var/log/messages e.g. If you like to inspect more logfiles in a comfortable way then go to System => System Administration => System Logfile Viewer. Or in case your menu structure differs from mine, at the command prompt launch **gnome-system-log**.

HTH,
Karl

---

### Post by blind2314 on 2011-03-30
Also, from a terminal (assuming you're comfortable/ok with that), use this:
 
```
last
```
 
 
That will show you the users who have logged on, when they've logged on, and where they logged on from (IP address or DNS name if applicable).

---

### Post by seawolf167 on 2011-03-30
+1 for *last* - sounds like exactly what you are looking for

---

### Post by welshmike on 2011-03-31
Many thanks everyone.
I learn a little every day.

---

### Post by Rubi1200 on 2011-03-31
In the terminal:

```
lastlog
```

edit: last command is much more useful

---

