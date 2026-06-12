---
title: "How to browse a mounted device (flash drive) via command line?"
date: 2012-09-18
forum: General Help
---

### Post by linuxvstheworld on 2012-09-18
Is there a way to jump on a flash drive and browse through it the same way you'd browse through documents via the command line?

---

### Post by sandyd on 2012-09-18
its in /media
```

cd /media
ls

```

---

### Post by linuxvstheworld on 2012-09-19
I've done that and it is there when I do ls, can't I just cd into it now?

---

### Post by cjhabs on 2012-09-19
> **linuxvstheworld said:**
> I've done that and it is there when I do ls, can't I just cd into it now?
 
You can cd to it:
cd /media/abcdef (or whatever it was mounted as)
or you can list it:
ls -l /media/abcdef
or both:
cd /media/abcdef
ls -l

---

### Post by linuxvstheworld on 2012-09-19
> **cjhabs said:**
> You can cd to it:
cd /media/abcdef (or whatever it was mounted as)
or you can list it:
ls -l /media/abcdef
or both:
cd /media/abcdef
ls -l

What if there's a space in the flash drive name? Don't I just do the back slash trick to signify a space? 
Will it work like this?
```
cd /media/JOEY'S\16GB
```

---

### Post by windscape on 2012-09-19
Hi,

That should work or you can enclose it in quotes such as ```
cd "/media/Joey's 16GB"
```

---

### Post by linuxvstheworld on 2012-09-19
> **windscape said:**
> Hi,

That should work or you can enclose it in quotes such as ```
cd "/media/Joey's 16GB"
```

Oh ok I'll try it when I'm near my Ubuntu computer, thanks!

---

