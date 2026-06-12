---
title: "Can't save any files!"
date: 2010-02-09
forum: General Help
---

### Post by nothingface1 on 2010-02-09
I am very new to linux but not to computers. The transition from Windows to Ubuntu was seamless, it is very easy to use and I really like linux so far, until it came time to save a file. I find it very hard to believe that every time you create a document of file that you need to be logged in as root to save it or at least that's what everyone is telling me. I need help this is very frustrating!

Thanks, B

---

### Post by wojox on 2010-02-09
You can do anything to a file in your user directory, but outside of that you need root privileges. That's the security of Linux.

---

### Post by Morbius1 on 2010-02-09
Where are you trying to save the file?

If it's somewhere in you own home folder then you don't need to be root.

If it's somewhere else then you do.

Give the full path to where you're trying to save the file.

[COLOR=Blue]EDIT: OOPS: Sorry --- what wojox said[/COLOR]

---

### Post by nothingface1 on 2010-02-09
> **Morbius1 said:**
> Where are you trying to save the file?

If it's somewhere in you own home folder then you don't need to be root.

If it's somewhere else then you do.

Give the full path to where you're trying to save the file.

[COLOR=Blue]EDIT: OOPS: Sorry --- what wojox said[/COLOR]


/var/www/index.html for example

---

### Post by wojox on 2010-02-09
Then you need:

```
gksudo gedit /var/www/index.html
```

---

