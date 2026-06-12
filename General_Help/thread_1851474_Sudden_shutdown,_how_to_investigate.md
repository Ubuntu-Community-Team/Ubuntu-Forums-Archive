---
title: "Sudden shutdown, how to investigate"
date: 2011-09-28
forum: General Help
---

### Post by Sidrabs on 2011-09-28
Hello,

This happened to my Ubuntu 11.04 (classic Gnome interface) install twice: I have several apps open, and suddenly my laptop goes in shutdown, without letting me save my open documents etc. I can see the terminal screen with some info about termination signal, but it flashes only briefly, so I can not tell here what it was.

How can I investigate this, please? Where in the logs could I find some reason of such automatic shutdown? Could it be processor overheating perhaps?

---

### Post by 2F4U on 2011-09-28
Do you know the approximate time when this happened? If yes, look into the log file and locate the approximate time. Look for messages shortly before the time of shutdown. It may help if you post the messages here.

---

### Post by Sidrabs on 2011-09-28
Please specify, which log file you mean, and where to find it.

---

### Post by 2F4U on 2011-09-28
You should look into 

/var/log/syslog

first. There may be others, for example /var/log/syslog.1, since this file is rotated if it reaches a particular size. So, depending on far away from now the date you are looking for is, you may need to check other files.

---

### Post by Sidrabs on 2011-09-28
Ok, there it is:

```
Sep 28 18:19:22 Prodigy kernel: [15538.371512] intel ips 0000:00:1f.6: MCP limit exceeded: Avg temp 10099, limit 9000
Sep 28 18:19:22 Prodigy kernel: [15538.860509] Critical temperature reached (100 C), shutting down.
Sep 28 18:19:23 Prodigy kernel: Kernel logging (proc) stopped.
Sep 28 18:19:23 Prodigy rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="831" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

So, apparently, something has gone wrong with the temp regulation. This has never happened before, even in the hot summer days.

Does that mean I should worry now? Get some temperature monitoring widget and worryingly eye it? Any suggested apps?

---

### Post by collisionystm on 2011-09-28
Open your case and blow all the dust out of it. Be sure to clean the heat sink. Make sure your fans are working correctly.

---

### Post by collisionystm on 2011-09-28
Sorry mis-read that it was a laptop. Check your Vents to see if they are clogged. Is your fan turning on?

---

### Post by Sidrabs on 2011-09-28
Yes, the fan is pretty much running all the time. Can you suggest me some good temp and fan monitoring app?

---

