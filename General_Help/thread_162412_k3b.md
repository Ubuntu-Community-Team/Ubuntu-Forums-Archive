---
title: "k3b"
date: 2006-04-18
forum: General Help
---

### Post by Hoffmann on 2006-04-18
Hello:

All the time I try to burn a data CD with k3b, I get the error:

"Cdrecord has no permission to open the device"

Could anyone, please, help me to set that up?

Thanks,
Hoffmann

---

### Post by jazzmuzik on 2006-04-18
I believe you need to go into Settings, K3b Setup. There should be an option there to grant greater rights to cdrecord.

---

### Post by Hoffmann on 2006-04-19
[QUOTE=jazzmuzik]I believe you need to go into Settings, K3b Setup. There should be an option there to grant greater rights to cdrecord.[/QUOTE]

Sorry, if that seems to be 'stupid', but I still didn't solve my k3b problem. I see no way to change that permission. It works just if I lounch k3b as 'root" (actually, sudo k3b).

Hoffmann

---

### Post by twigboy on 2006-04-19
search the repositories for gksudo. Then install it.  It will act the same as when you first open up synaptic and it asks for your password, but it will do it for k3b.  I had the same problem and gksudo solved it.

---

### Post by Hoffmann on 2006-04-19
[QUOTE=twigboy]search the repositories for gksudo. Then install it.  It will act the same as when you first open up synaptic and it asks for your password, but it will do it for k3b.  I had the same problem and gksudo solved it.[/QUOTE]

With gksudo, will I have any 'conflict' with the normal sudo? I mean, how gksudo works?

---

### Post by richardward101 on 2006-04-19
gksudo should be fine alongside sudo, its just the graphical version of sudo, so it gives you a box to type into instrad of it being in a terminal

---

### Post by Hoffmann on 2006-04-19
[QUOTE=richardward101]gksudo should be fine alongside sudo, its just the graphical version of sudo, so it gives you a box to type into instrad of it being in a terminal[/QUOTE]

By searching by gksudo on Synaptic, I found gnome-sudo. Is that the same?

---

### Post by jazzmuzik on 2006-04-20
They are the same. Both gksudo and gnome-sudo merely point to gksu, which is the actual program. Run this to see:

ls -l /usr/bin/gksu*
ls -l /usr/bin/gnome-sudo
more /usr/bin/gnome-sudo

---

