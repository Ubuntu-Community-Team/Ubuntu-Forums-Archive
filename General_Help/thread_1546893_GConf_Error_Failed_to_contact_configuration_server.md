---
title: "GConf Error: Failed to contact configuration server;"
date: 2010-08-06
forum: General Help
---

### Post by davidbr on 2010-08-06
Hello,


I am a linux newbie but so far I enjoy it very much. 



I use Ubuntu 10.04, and the problem is that every now and then I start getting the following messages when starting, or example, gedit:

  [INDENT]   GConf Error: Failed to contact   configuration server; some possible   causes are that you need to enable   TCP/IP networking for ORBit, or you   have stale NFS locks due to a system   crash. See   [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for   information. (Details -  1: Server   ping error:   IDL:omg.org/CORBA/COMM_FAILURE:1.0)
 [/INDENT]  I did some searching and read suggestions to ```
rm ~/.dbus*
``` or ```
mv ~/.gconfd/saved_state ~/.gconfd/.saved_state
``` but these do not work for me.


Thank you,

---

