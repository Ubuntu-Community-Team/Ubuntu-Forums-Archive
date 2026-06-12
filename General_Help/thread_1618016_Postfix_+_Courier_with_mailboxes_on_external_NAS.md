---
title: "Postfix + Courier with mailboxes on external NAS"
date: 2010-11-10
forum: General Help
---

### Post by Sansone on 2010-11-10
Hi everybody,
 I've succesfully installed on Ubuntu 10.10 both Postfix & Courier using virtual users to manage all my intranet emails through IMAP.
All emails are recorded under my local folder /mnt/mail/....and I have no problem.
But if I really mount my mail shared folder from my QNAP NAS in the same place then Postfix still works but Courier fails.
See some lines from /var/log/mail.log:

Nov  8 13:16:13 main authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/mnt/mail/virtual, address=sansone@sansone.local, fullname=sansone, maildir=/mnt/mail/virtual/sansone$
Nov  8 13:16:13 main imapd: LOGIN, user=sansone@sansone.local, ip=[::ffff:192.168.168.203], port=[54623], protocol=IMAP
Nov  8 13:16:13 main imapd: rename(./new/1289056090.V16I90001ba0006M547961.main,./cur/1289056090.V16I90001ba0006M547961.main:2,) failed: No such file or directory

As you can see the imapd fails the rename from folder New to Cur in spite it's correctly authenticated.

Any hint ?

Thanks & regards.
Sans1

---

