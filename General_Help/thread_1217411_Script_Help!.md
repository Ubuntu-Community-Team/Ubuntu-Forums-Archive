---
title: "Script Help!"
date: 2009-07-19
forum: General Help
---

### Post by Psycho.mario on 2009-07-19
Whenever i run this command:
```
gksudo "sh -c 'echo "$final" >> /etc/fstab'"
```
in a terminal, it succeeds. However, when i try to run it in my script, it fails. It is not to do with the $final variable, that is set properly, it completely fails to write to fstab.
Thanks in advance

---

### Post by TeoBigusGeekus on 2009-07-19
Someone correct me if I'm wrong, but I think it has to do with the gksudo part. You can't run a script that asks for root permission during the execution of its commands.

---

