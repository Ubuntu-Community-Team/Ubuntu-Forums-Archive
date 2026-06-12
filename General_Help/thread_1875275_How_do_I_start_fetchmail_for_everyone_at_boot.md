---
title: "How do I start fetchmail for everyone at boot?"
date: 2011-11-04
forum: General Help
---

### Post by AlexBooton on 2011-11-04
Hi,

I've asked before and tried some suggestions but still can't get this to work.

I want fetchmail to start for all users at boot.  

I've tried putting the following line in /etc/rc.local

[INDENT]fetchmail -d 60 -f /etc/fetchmailrc[/INDENT]

but it doesn't start at boot!?

The fetchmailrc file is in /etc. It is owned by fetchmail with rw privileges.

What am I doing wrong?  How can I get this to work?

Thanks,

AB

---

### Post by AlexBooton on 2011-11-07
Isn't there anyone here that knows what's wrong and how to fix it?

Thanks,

AB

---

### Post by glennr on 2012-01-07
To start the system wide fetchmail you use /etc/default/fetchamail .

Just add a line
```
START_DAEMON=yes
```

This will run the config in /etc/fetchmailrc .

---

