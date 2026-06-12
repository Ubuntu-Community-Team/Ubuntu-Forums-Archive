---
title: "Why does this program fail to work?"
date: 2012-08-12
forum: General Help
---

### Post by eddie3000 on 2012-08-12
I have Ubuntu studio 12.04 installed, that comes with xfce desktop. I installed Expoblending, it's worked for me in the past, but I've never used it in 12.04. I get this message when trying to start it. Anybody know why?

"Failed to execute command "expoblending %i -caption %c %U"."

"Failed to execute child process "expoblending" (No such file or directory)"

Thanks.

---

### Post by sienile on 2012-08-12
It appears that it's not in a $PATH directory. Try:
```
which expoblending
```
If it's in a defined path it should give the full path to the file. If not, you need to type the full path whenever you run the program... Or add it's directory to the path.

---

