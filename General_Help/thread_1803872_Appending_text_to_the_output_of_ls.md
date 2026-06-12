---
title: "Appending text to the output of ls"
date: 2011-07-14
forum: General Help
---

### Post by lawrencejohny on 2011-07-14
I was wondering if it is possible to append some text to the output of ls. Like say, if i wanted to create symbolic links for all the files under a folder in my hard disk to a folder on my desktop, I could say (Pretty sure this won't work, but I am looking forward to something like this) echo ln -s | ls . This should append ln -s to all the files of ls. 

Any help is much appreciated.

---

### Post by Vaphell on 2011-07-14
```
for file in /home/username/*; do if [ -f "$file" ]; then echo ln -s "$file"; fi; done

```

You should avoid using command outputs for such things, because whitespaces in names will make you pull your hair out more often than not.

---

### Post by lawrencejohny on 2011-07-14
> **Vaphell said:**
> ```
for file in /home/username/*; do if [ -f "$file" ]; then echo ln -s "$file"; fi; done

```

You should avoid using command outputs for such things, because whitespaces in names will make you pull your hair out more often than not.
Thanx. Worked perfectly. Will keep in mind about the whitespaces.

---

