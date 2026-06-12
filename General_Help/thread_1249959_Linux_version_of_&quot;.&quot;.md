---
title: "Linux version of &quot;*.*&quot;"
date: 2009-08-26
forum: General Help
---

### Post by e24ohm on 2009-08-26
Folks,
what is the linux versino of "*.*"? I am trying to build a tar script that will archive everything in the current directory.

tar -czvf test.tgz *.*

doesn't work, so I need the the wildcard for the linux version thanks.

---

### Post by nima_a on 2009-08-26
Hi,
```
 tar -cvf something.tar * 
```

---

### Post by credobyte on 2009-08-26
```
*.txt - all text files
file.* - all file types with the name "file"
* - all files

```

---

### Post by e24ohm on 2009-08-26
> **nima_a said:**
> Hi,
```
 tar -cvf something.tar * 
```thanks...this really helps out.

---

### Post by e24ohm on 2009-08-26
> **credobyte said:**
> ```
*.txt - all text files
file.* - all file types with the name "file"
* - all files

```oh ok...I see the syntex now...thank you.

---

