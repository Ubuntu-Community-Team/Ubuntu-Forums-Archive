---
title: "How to set a commands output to a variable in a shell script"
date: 2010-10-28
forum: General Help
---

### Post by lukemk1 on 2010-10-28
Hi guys so the title explains it. What I'm trying to do is set the current date equal to a variable so I can create a directory that in the name has the date so that I can save backups for that day.

I've tried a few different ways that I thought would have worked but none of them worked. I'm sure this is simple but I just can't get it working...

---

### Post by TeoBigusGeekus on 2010-10-28
```
d=$(date)
```
See man date for different formats.

---

### Post by blur xc on 2010-10-28
or you can use back-tics..  dunno what's preferred.

```
d=`date`
```

but you also may have to take into account for special characters in the output of whatever command you are running (iirc, it's been a while):
```

x="`some command that generates special characters in its output`"
```

I've been burned on that one before...

BM

---

### Post by lukemk1 on 2010-10-28
Thanks guys I got it now.

---

### Post by Stephen Morgan on 2010-10-28
```
mkdir $(date %Y-%m-%d)
```

---

