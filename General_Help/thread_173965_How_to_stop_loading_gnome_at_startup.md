---
title: "How to stop loading gnome at startup?"
date: 2006-05-11
forum: General Help
---

### Post by Jabran Asghar on 2006-05-11
Hi,

I am using Ubuntu since some time. Have end-up realising that I dont need gnome most of the time --- command line works like a charm :) 

How can I can stop gnome/x and related services from being loaded automatically at startup. I want only text based login on startup, and then to be able to start Gnome with "startx" when required.


Thanks.

Jabran

---

### Post by lol on 2006-05-11
simply remove the links to the startup scripts for any display manager from /etc/rc2.d

You can do it manually, but the best way to do that is probably to use 'update-rc.d':
```

update-rc.d -f gdm remove

```

---

### Post by Jabran Asghar on 2006-05-11
I looked at update-rc.d and it seems to do the task :)

Thanks.

---

### Post by Jabran Asghar on 2006-05-11
[QUOTE=Jabran Asghar]I looked at update-rc.d and it seems to do the task :)

Thanks.[/QUOTE]
and I found another useful commnad:

$w

yes, just "w" and it displays more useful information including IP, user idle time, and active program of each user.

---

### Post by Jose Catre-Vandis on 2006-05-12
[QUOTE=lol]simply remove the links to the startup scripts for any display manager from /etc/rc2.d

You can do it manually, but the best way to do that is probably to use 'update-rc.d':
```

update-rc.d -f gdm remove

```[/QUOTE]

Thanks, I needed that :-)

---

