---
title: "Remote Application Display Error"
date: 2009-09-14
forum: General Help
---

### Post by jverge on 2009-09-14
I have several Ubuntu 9.04-32bit Desktop systems which log into an Ubuntu 9.04-64bit Server either via ssh or rsh (its an internal network so rsh is fine).  I can only display matlab remotely on the desktops.  When I try to display gedit or firefox I get the following error:

"GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)"

Some users have NFS home directories and others do not, both have the same display problem.  This error comes up a lot in GOOGLE but the solution eludes me.  

Any suggestions??

---

### Post by jverge on 2009-09-17
Anyone have any ideas?

---

