---
title: "ssh-add not working"
date: 2011-10-26
forum: General Help
---

### Post by cmcnamara on 2011-10-26
I am attempting to add an ssh key using ssh-add. Upon running ssh-add ~/.ssh/insertkeynamehere I am prompted with:

```
Could not open a connection to your authentication agent.

```
After doing some research it would appear as if this is because my ssh-agent is not running but ps -ef | grep ssh-agent indicates otherwise:

```
cdm       1760  1727  0 14:35 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
```

Even after running:

```
exec ssh-add bash

```
And seeing:

```
cdm       1760  1727  0 14:35 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=classic-gnome
cdm       2903     1  0 14:45 ?        00:00:00 ssh-agent
```

This problem persists. Any help would be must appreciated and if you need to see anymore console output let me know and I'll be happy to post.

---

