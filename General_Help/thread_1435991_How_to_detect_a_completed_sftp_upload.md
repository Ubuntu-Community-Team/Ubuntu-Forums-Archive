---
title: "How to detect a completed sftp upload"
date: 2010-03-22
forum: General Help
---

### Post by tokyojb on 2010-03-22
Hi all,

I'm writing a file handler script that monitors (via a cron job) a directory that is an openssh sftp target for new files. When it detects a new file, it moves it, does an scp to another system, and sends an email. 

The problem I have is that I can't figure out a way to verify that the sftp upload is complete before I start manipulating the file. 

Does anybody have an idea?

(I'm doing this on Ubuntu Server 9.10)

Thanks

JB

---

### Post by amauk on 2010-03-22
check file size
wait 30 seconds
check file size again
if 2 sizes equal, then finished

---

