---
title: "Huge log files"
date: 2011-07-04
forum: General Help
---

### Post by Extrm3 on 2011-07-04
I streamed video through a my computer with mediatomb yesterday. The problem is that now, I got these huge log files. I am running out of memory (less than 1 gb left) as we speak.

They're filled with ufw entries, but my question is:

I read somewhere about a program called logrotate that were supposed to keep logs from getting to big, is this wrong and should mediatomb generate 3 separate log files with 5gb of data each for just 2 hours of streaming?

---

### Post by SeijiSensei on 2011-07-04
First figure out why you're getting log entries from iptables.  How about posting an example inside [noparse][code][/noparse] tags.

logrotate runs once daily; it won't archive logs in real-time.  It also won't rotate logs for which there's no configuration file in /etc/logrotate.d/.

---

### Post by Extrm3 on 2011-07-04
I deleted the logs since it made me a little worried about running out of space.

I had ufw logging on full and the last lines of the syslog was just a lot of ufw[audit], ufw [blocked]. I have set the logging to medium and I'm not planning on running mediatomb on this computer again.

I will see if the problem comes back again. I just wanted to know if my logrotate was malfunctioning.

---

