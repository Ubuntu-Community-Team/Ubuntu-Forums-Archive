---
title: "rsync warning: file has vanished"
date: 2010-03-24
forum: General Help
---

### Post by snake_eyes on 2010-03-24
Hello,

I'm always getting this error when I run the rsync command:
```
sending incremental file list
file has vanished: "/home/user/webserver/www/upload/attachments/13798447104b7f994148145.____.pdf"
```
when I try to navigate the file:
```
ls -lh /home/user/webserver/www/upload/attachments/13798447104b7f994148145.____.pdf
```
it gives
```
ls: cannot access /home/user/webserver/www/upload/attachments/13798447104b7f994148145.____.pdf: No such file or directory
```

Is there any idea regarding to this matter?

Cheers,

---

### Post by rnerwein on 2010-03-24
hi
that's exactly what vanished means. i guess it's not always the same filename. the name looks like
a temporary file.
ciao

---

### Post by snake_eyes on 2010-03-24
what I supposed to do in order to avoid such as this?

Please note that I'm facing this when I formated my pc.. but before I didn't

Cheers,

---

