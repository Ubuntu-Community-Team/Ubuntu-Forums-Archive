---
title: "Got a weird problem with nautilus"
date: 2006-01-31
forum: General Help
---

### Post by Wolfbite on 2006-01-31
Hi, when typing "sudo nautilus" in terminal (whether superuser or not), I get the message:

```
(nautilus:11138): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

And then it proceeds to the file browser. I'd like to fix this. That means I need YOU to fix this. ^^

---

### Post by Wolfbite on 2006-01-31
Bump! :)

---

### Post by z_diver on 2006-01-31
Are you getting this message while working in a local terminal or when sshing into a remote box?  I am unable to reproduce this either way although I believe I have seen it before.  Maybe some details will refresh my memory.

---

### Post by Wolfbite on 2006-02-01
[QUOTE=z_diver]Are you getting this message while working in a local terminal or when sshing into a remote box?  I am unable to reproduce this either way although I believe I have seen it before.  Maybe some details will refresh my memory.[/QUOTE]

I have no clue as to what sshing is, but I suppose I use a local terminal, yes. What I do know is that this error didn't happen before, and it prevents me from doing superuser magic in the file browser.

---

### Post by Jason_25 on 2006-02-01
Every Ubuntu install I have seen has this problem.

```

sudo -s
nautilus

```

should do it without an error.

---

### Post by Wolfbite on 2006-02-04
Hey, that seemed to work. Thanks a lot! :)

---

