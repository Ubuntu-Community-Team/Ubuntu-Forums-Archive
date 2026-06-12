---
title: "how to recover ubuntu files(install in window)"
date: 2011-11-02
forum: General Help
---

### Post by clapika on 2011-11-02
my ubuntu 10.10(install in window) just got grub problem and i need some files in it, can i get it back?
pls help me~

---

### Post by Script Warlock on 2011-11-02
you can use the live cd/usb to recover those files.

---

### Post by clapika on 2011-11-02
but my dvd rom also got problem cant read cd.can i recover from root.disk files?

---

### Post by Script Warlock on 2011-11-02
you can use the usb stick

---

### Post by clapika on 2011-11-02
i'm on live usb now but where is my file?i cant find it

---

### Post by clapika on 2011-11-02
thx by the way , i use mount command to run root.disk :)

---

### Post by alquery on 2011-11-02
> **clapika said:**
> thx by the way , i use mount command to run root.disk :)

So you have the disk with your file on it mounted, but you can't find it? If your problem is that you don't remember the folder it's in, you can use this terminal command:

```
find <path-to-your-disk-here> -iname <part-of-the-name-of-your-file> 2>/dev/null
```

---

### Post by clapika on 2011-11-02
> **alquery said:**
> So you have the disk with your file on it mounted, but you can't find it? If your problem is that you don't remember the folder it's in, you can use this terminal command:

```
find <path-to-your-disk-here> -iname <part-of-the-name-of-your-file> 2>/dev/null
```

solved already thx by the way :)

---

### Post by alquery on 2011-11-03
> **clapika said:**
> solved already thx by the way :)

You can mark it as "solved" then (in thread tools) so people know that your problem's fixed

---

