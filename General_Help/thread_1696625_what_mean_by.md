---
title: "what mean by?"
date: 2011-02-27
forum: General Help
---

### Post by pua06 on 2011-02-27
salmo allikm wa rhmat allah wa brakato

i am new in field linux (ubunto 10.10)
that my question when i unmounted my hard disk and do fdisk for it
that the message that i don't know what mean and why i get

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
please want details what mean and if i don't follow what said what will happen?
thanks

---

### Post by cchhrriiss121212 on 2011-02-27
It recommends you use some options, like this:
```
sudo fdisk -c -u -l
```

No big deal, there are no consequences of ignoring these options.

---

