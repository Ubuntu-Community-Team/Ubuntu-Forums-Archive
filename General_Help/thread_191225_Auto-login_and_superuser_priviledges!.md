---
title: "Auto-login and superuser priviledges!"
date: 2006-06-07
forum: General Help
---

### Post by daller on 2006-06-07
Hi There,

How do I make a certain user login automatically?

And when that user is logged in, he should have superuser priviledges to run "/usr/bin/sispm" (and the processes that application starts!)

Even by running "sudo visudo" and writing the following, doesn't work!

USER ALL=(ALL) ALL

What else should I do?

---

### Post by norman_ on 2006-06-09
auto-login: xfce menu --> System --> Login Window --> Security --> Enable automatic login.

I don't understand what you mean about privileges for sispm. for me, whenever I use sudo <command> it gives me all superuser privileges for that action...

---

### Post by daller on 2006-06-10
[QUOTE=norman_]
I don't understand what you mean about privileges for sispm. for me, whenever I use sudo <command> it gives me all superuser privileges for that action...[/QUOTE]

It should be permanent! (not asking for password!)

---

