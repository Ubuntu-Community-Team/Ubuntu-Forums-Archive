---
title: "Software"
date: 2009-12-04
forum: General Help
---

### Post by usmanasim on 2009-12-04
Hello Ubuntu Guys,

I just downloaded a software for linux which is of type bin.

How do install it can anybody please give me detailed commands for Terminal.

---

### Post by oldos2er on 2009-12-04
What program is it? Have you checked to see if it's in the repositories?

---

### Post by elliotn on 2009-12-04
ya specify n have never had a program in .bin before

---

### Post by gmjs on 2009-12-04
'bin' is short for binary, so it will probably run at the terminal (occasionally they're compressed and extract themselves like a WinZip self-extracting executable file under Windows).

For example, Java supply the Linux version of their Java Runtime Environment in this format for installing at the terminal.

All you'll need to do is set the execute bit and run the file at the **Terminal**:

```
$ **cd /path/to/the/file**
$ **chmod +x filename-here.bin**
$ **./filename-here.bin**
```

Hope that helps.

Graham

---

### Post by usmanasim on 2009-12-04
Thanks

The previous post helped.

---

