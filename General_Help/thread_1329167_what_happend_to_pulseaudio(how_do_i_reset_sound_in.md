---
title: "what happend to pulseaudio(how do i reset sound in 9.10)"
date: 2009-11-17
forum: General Help
---

### Post by rhythmiccycle on 2009-11-17
some time my sound stops working, and I used to fix it with
```

$sudo killall pulseaudio 
$ pulseaudio 

```

but in 9.10 I after typing pulseaudio i get 

```

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

so how do i reset sound in 9.10?

---

### Post by klemes on 2009-11-17
Try :

```
sudo pulseaudio -D --kill
```

---

### Post by rhythmiccycle on 2009-11-19
this is what i get

```

mike@mike-desktop:~$ sudo pulseaudio -D --kill
[sudo] password for mike: 
E: core-util.c: Home directory /home/mike not ours.
E: main.c: Failed to kill daemon: Permission denied

```

---

