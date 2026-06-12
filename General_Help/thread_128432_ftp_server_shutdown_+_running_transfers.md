---
title: "ftp server shutdown + running transfers"
date: 2006-02-11
forum: General Help
---

### Post by wildfox on 2006-02-11
Strange thing happened, and i couldn't find any useful information with google, so here it goes:
 I have pure-ftpd running (starts with boot) on my ubuntu. A user was uploading a bigger file (~500 Mbytes). I had to restart (the transfer was running), but when i returned into ubuntu the file's gone. Now, if a user cancels a transfer it can continue later, the incomplete file stays in the user's home. So why has the file disappeared now when the server canceled it (stopped)?
 I couldn't find any info about the file in syslog, messages or in pure-ftpd's transfer.log.
 What do i have to setup to store the incomplete files when i shut down the ftp-server? I've been using pure-ftpd for quite a long time now, but are there any other ftp-servers, that can do the  trick (e.g. ProFtp) ?

---

