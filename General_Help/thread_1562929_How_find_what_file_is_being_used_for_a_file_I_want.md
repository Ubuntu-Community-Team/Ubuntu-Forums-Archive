---
title: "How find what file is being used for a file I want deleted?"
date: 2010-08-28
forum: General Help
---

### Post by orangecakz1 on 2010-08-28
I want to delete a file but it says it's in use by another program. I forgot what the command was to look for it.

---

### Post by ronnielsen1 on 2010-08-28
What file are you trying to delete?

---

### Post by orangecakz1 on 2010-08-28
> **ronnielsen1 said:**
> What file are you trying to delete?
A .app application

---

### Post by ronnielsen1 on 2010-08-28
> A .app application 	

A program? An .app extension? Is this in your /home? If you're trying to remove a package

[CENTER][COLOR=Blue][I][B][Click here]("https://help.ubuntu.com/9.10/add-applications/C/removing.html")
[/B][/I][/COLOR][/CENTER]

---

### Post by Toz on 2010-08-28
Try:

lsof | grep <filename>

/ToZ

---

