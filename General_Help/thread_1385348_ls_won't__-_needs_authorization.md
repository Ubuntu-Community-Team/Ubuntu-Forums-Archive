---
title: "ls won't  - needs authorization"
date: 2010-01-19
forum: General Help
---

### Post by Vaclav Vasek on 2010-01-19
As a administartor I can  do ls on root, but when I cd to /media ls does not work - blank respoonse. I have to sign in GUI file manager and authenticate to make ls work.
Do I need to be at root? And why???

---

### Post by michy99 on 2010-01-19
ls should work in /media. How are the permissions set?```
ls -ld /media
```

---

### Post by bodhi.zazen on 2010-01-19
> **Vaclav Vasek said:**
> As a administartor I can  do ls on root, but when I cd to /media ls does not work - blank respoonse. I have to sign in GUI file manager and authenticate to make ls work.
Do I need to be at root? And why???

Blank response == success. The directory may be empty.

If you are getting an error message, please post it.

---

