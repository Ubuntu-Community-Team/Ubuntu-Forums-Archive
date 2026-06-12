---
title: "Network activity monitor"
date: 2009-09-23
forum: General Help
---

### Post by Trifid on 2009-09-23
Does anyone know of a real time monitoring program (with the ability to record?)connections through a Ubuntu PC running Squid?

Something like Etherape but a bit more definate? I get flooded with the VNC connection taking up most of the screen (perhaps it is a bit too graphical?)

Thanks.

---

### Post by mentalelf on 2009-09-23
You could just use terminal to keep an eye on the log files in real-time?

After installing squid here there are three log files...

/var/log/squid/access.log

/var/log/squid/cache.log

/var/log/squid/store.log

so if you run...

tail -f /var/log/squid/access.log

...it'll show you the last few lines of that log file, & update live.

If you want it on your desktop so you can keep an eye on things you can probably use some monitoring script for conky.

Recording-wise, it's all in the logs, which'll get rotated every now & then. (weekly?)

---

