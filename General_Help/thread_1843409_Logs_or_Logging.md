---
title: "Logs or Logging"
date: 2011-09-13
forum: General Help
---

### Post by alan89 on 2011-09-13
Hi Guys,

Using Ubuntu 11.04 for the past few months and no problems. Since  the weekend it keeps freezing/crashing.

Three things happen:
1) Screen freezes mouse doesn't move. (Hard light on laptop is not solid)

2) Screen goes black as if it was off but laptop stay's turned on. Doesn't respond to any keyboard/mouse events

3) Screen goes black for a second/two and it brings me to the login screen but when I log in its as if the computer restarted as everything is closed.

Is there a way for me to enable/view logs to see what happened?
I had a look at the log file viewer but I am not sure where or what I should be looking at.

Any help appreciated!

---

### Post by aeiah on 2011-09-13
try /var/log/messages

logs are rotated, so when /var/log/messages gets full, it gets moved to /var/log/messages.1 and /var/log/messages starts a fresh, etc.

there's also /var/log/syslog which is more thorough, but /var/log/messages is probably the first port of call.

probably easiest to do it in a terminal:
```

cat /var/log/messages

```

---

### Post by raja.genupula on 2011-09-13
+1
```
dmesg
``` also going to have log

---

### Post by 2F4U on 2011-09-13
/var/log/Xorg.0.log may show errors with respect to the desktop environment.

---

### Post by raja.genupula on 2011-09-13
> **2F4U said:**
> /var/log/Xorg.0.log may show errors with respect to the desktop environment.

thanks for this , i will remember this .

---

### Post by 2F4U on 2011-09-13
Another file you may want to look into is .xsession-errors. It is a hidden file in your /home directory.

---

### Post by fdrake on 2011-09-13
everything you are looking for is in > /var/log/*
but in specific you should look into;
> messages
kern.log
syslog
user.log
Xorg.0.log
u better do some egrep filtering unless you have some time to waste in reading all the logs.

---

