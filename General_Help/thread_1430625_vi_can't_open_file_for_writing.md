---
title: "vi: can't open file for writing"
date: 2010-03-15
forum: General Help
---

### Post by yawnmoth on 2010-03-15
I'm trying to edit a file in vi and when I hit  Esc and type in :w I get the following error:

> "test.sh" E212: Can't open file for writing

Here are the permissions of the directory I'm trying to save the file to: drwxr-xr-x

Any ideas?

---

### Post by blur xc on 2010-03-15
> **yawnmoth said:**
> I'm trying to edit a file in vi and when I hit  Esc and type in :w I get the following error:



Here are the permissions of the directory I'm trying to save the file to: drwxr-xr-x

Any ideas?

Are you the owner of the directory?

BM

---

### Post by yawnmoth on 2010-03-15
> **blur xc said:**
> Are you the owner of the directory?

BM

I thought I was but apparently I wasn't logged in as the user I thought I was.  Doing "su - correctuser" fixed the problem.

---

