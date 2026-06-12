---
title: "Clearing system logs"
date: 2011-07-11
forum: General Help
---

### Post by H3110 on 2011-07-11
Hi Guys,

I would like to run a process where at 00:00:00 every day I compress each and every log file in /var/log into a zip archive and move into a folder which can be downloaded using SFTP.

However there are two main reasons to do this:

1. Consume the disk-space used by the logs (accumulated over time).
2. The smaller the file, the faster the server can write to them.

I **DO NOT** want to _delete_ but simply _move_ them to another distination via a zip archive by date.

yyyy-mm-dd.logs.zip

could anyone assist me with this issue?

Thanks!

---

### Post by Gyokuro on 2011-07-11
Hi,

have a look at **logrotate** - more info at: [http://linuxcommand.org/man_pages/logrotate8.html](http://linuxcommand.org/man_pages/logrotate8.html)

---

### Post by H3110 on 2011-07-15
Thanks for the post; this is exactly what I seek!

---

