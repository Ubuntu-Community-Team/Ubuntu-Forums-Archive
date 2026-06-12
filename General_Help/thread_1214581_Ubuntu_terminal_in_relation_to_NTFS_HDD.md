---
title: "Ubuntu terminal in relation to NTFS HDD"
date: 2009-07-16
forum: General Help
---

### Post by Azuu on 2009-07-16
I have a second storage hdd, and I need to use terminal to get to it from time to time. The issue stems from the fact that my extra HDD is named "Alex's Main" and "Alex's storage". Terminal can not reach it (as far as i know), and I have some very large files of storage data that cannot be moved. That issue leaves out reformating it from my options. Is there any way to rename them?

---

### Post by PureLoneWolf on 2009-07-16
You can use backslashes to help in terminal.

cd Alex\'s\ Storage from the parent, should get in there.  It depends on where you mounted it though.

Hope that helps a little

---

### Post by Azuu on 2009-07-17
> **PureLoneWolf said:**
> You can use backslashes to help in terminal.

cd Alex\'s\ Storage from the parent, should get in there.  It depends on where you mounted it though.

Hope that helps a little

that doesn't,
> > cd /media/Alex's/storage
bash: cd: /media/Alex/s/storage
cd /media/Alexs/storage: No such file or directory

it either does that or it gives me a blank > until I ctrl+c
thank you for your attempt.

---

### Post by zaphod777 on 2009-07-17
> **Azuu said:**
> that doesn't,

it either does that or it gives me a blank > until I ctrl+c
thank you for your attempt.

try backslash not forward slash.

---

### Post by PureLoneWolf on 2009-07-17
Try

```
cd /media/Alex\'s\ Storage
```

I just tested this myself and it is fine, the backslash is the important thing

---

