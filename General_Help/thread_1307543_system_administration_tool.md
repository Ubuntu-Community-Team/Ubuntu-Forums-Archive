---
title: "system administration tool"
date: 2009-10-31
forum: General Help
---

### Post by quimkaos on 2009-10-31
i had in 9.04 an application in system>administration menu were i could see and restart system services... i'm not finding any packages for it in 9.10... does anyone knows the name of the program/package or anything similar.

What i'm trying to accomplish is simply to restart de apache server, that i know that i can do by console but i don't know the command.

any ideas?

---

### Post by 3rdalbum on 2009-10-31
Ubuntu 9.10 uses the Upstart system rather than the Init system; so the old Services program (and the BUM program) don't work anymore.

I think this should work:

```
sudo service /etc/init.d/apache2 graceful
```

But not tested, sorry.

---

### Post by quimkaos on 2009-10-31
i did

sudo service /etc/init.d/apache2 restart
and it worked...

tho i'm still looking for that sys admin tool...

---

