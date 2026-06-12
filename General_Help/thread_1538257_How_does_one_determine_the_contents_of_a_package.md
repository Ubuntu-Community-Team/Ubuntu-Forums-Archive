---
title: "How does one determine the contents of a package?"
date: 2010-07-24
forum: General Help
---

### Post by leonardevens on 2010-07-24
I am very experienced with versions of RedHat, including most recently Fedora.   Under these

rpm =ql  xxxx

will tell me the files which are part of package xxxx.

Recently, I started using ubuntu.

I haven't been able to figure out what the corresponding command(s) are for Ubunt

---

### Post by CharlesA on 2010-07-24
You mean dependencies?

```
dpkg-deb -I file.deb
```

---

### Post by howefield on 2010-07-24
Try

```
dpkg -c filename.deb
```

[http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php](http://www.cyberciti.biz/howto/question/linux/dpkg-cheat-sheet.php)

---

