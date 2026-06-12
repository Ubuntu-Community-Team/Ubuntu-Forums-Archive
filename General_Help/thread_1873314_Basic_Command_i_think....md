---
title: "Basic Command i think..."
date: 2011-11-01
forum: General Help
---

### Post by conradin on 2011-11-01
I have a folder for a website on my computer with server hundred thousand sub directories. How many? I don't know but I would like to know how many 1 level deep into the profiles/ folder. I cant open this in nautilus, because nautilus will crash. Is there a way to use the command line to know how many sub folders exist 1 level deep in the profiles/ folder?

---

### Post by Lars Noodén on 2011-11-01
You can count them with find and wc:
```

[find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html) ./profiles -type d -maxdepth 1 -print | [wc](http://manpages.ubuntu.com/manpages/oneiric/en/man1/wc.1posix.html) -l

```

If Nautilus is crashing be sure to file a bug report explaining how to crash it.

---

### Post by matt_symes on 2011-11-01
Hi

You can use

```
find /path/to/directory -maxdepth 1 -type d | wc -l
```

That is a small L after word count

This will give you all the directories incuding . and ..

You cange change the -maxdepth to different depths.

You can also use simething like.

```
ls -l /path/to/directory | grep "^d" | wc -l
```

That is a small L after ls.

This will only tell you the number of direct sub directories in a directory though and will not include . and ..

Try these options. They may need some tuning depending on the number of subdirectories you actually have.

Edit: Beaten to it.

Kind regards

---

### Post by conradin on 2011-11-01
77424.
Cool, I got it! Thank you Everyone!!!

---

