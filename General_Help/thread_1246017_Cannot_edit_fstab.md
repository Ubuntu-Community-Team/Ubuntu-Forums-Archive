---
title: "Cannot edit fstab"
date: 2009-08-21
forum: General Help
---

### Post by screaminfakah on 2009-08-21
Hello,
I tried to create a new swap file but when I went to edit the fstab file I could not get it to open properly. I used the command   ```
gksudo gedit /ect/fstab
```
and it opened a blank file??  Any ideas why the real file did not open?

Thanks

---

### Post by wojox on 2009-08-21
Try:

```
gksudo gedit /etc/fstab
```

---

### Post by screaminfakah on 2009-08-21
Hello Wojox

That is the command that I tried, see my first post, and it opened a blank file.

---

### Post by wojox on 2009-08-21
No you referenced ect not etc

---

### Post by Vaphell on 2009-08-21
nope, etc != ect

---

### Post by screaminfakah on 2009-08-21
Oops.
I was never good at spelling! :)
Thanks

---

### Post by 3rdalbum on 2009-08-21
Try installing the "nautilus-gksu" package. When you next log-in, you'll be able to right-click a file or a folder and choose "Open as Administrator". Saves on the typing and spell checking.

---

### Post by screaminfakah on 2009-08-21
Right on for the tip.  That program would make some things alot easier for me.

Thanks

---

