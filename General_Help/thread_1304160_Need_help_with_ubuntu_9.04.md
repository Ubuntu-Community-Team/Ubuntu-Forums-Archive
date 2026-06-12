---
title: "Need help with ubuntu 9.04"
date: 2009-10-29
forum: General Help
---

### Post by liaogz on 2009-10-29
Hi all,

I have some problems with ubuntu 9.04. while running gedit, it gives this error:

> GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

any help on this will be appreciated. thanks

---

### Post by bribera on 2009-10-29
I've encountered this issue before when remounting or wiping out /tmp -- in my case, it meant that the GConf configuration files that are normally stored there had been erased, but the daemon which expects them to exist is still running. It doesn't have smart enough error handling to recreate the required directories at this point in its life.

Try shutting down your gconf daemon using this command:

```
gconftool-2 --shutdown
```

It'll start up again the next time an application that needs to use gconf is started. When it starts, it's smart enough to create the missing directories.

Hope that's actually what your problem was...

---

