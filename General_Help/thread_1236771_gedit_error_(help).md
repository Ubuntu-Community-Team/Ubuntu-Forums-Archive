---
title: "gedit error (help)"
date: 2009-08-10
forum: General Help
---

### Post by loba09 on 2009-08-10
hi..
i try to edit my script and open gedit from teminal but i the error...

```
root@lobajr-hack:/# gedit test.sh

(gedit:10056): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```
how i fix it?
plz help:confused:

---

### Post by mcduck on 2009-08-10
Instead of starting gedit from a root terminal use normal terminal, with "gksudo" if the file requires root permissions for editing.

---

### Post by loba09 on 2009-08-18
emmm i see the different gksudo n sudo...
and root teminal for editing (gedit)...thanks a lot my friends..:guitar:

---

