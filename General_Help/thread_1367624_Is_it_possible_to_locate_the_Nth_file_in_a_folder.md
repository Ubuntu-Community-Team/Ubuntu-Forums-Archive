---
title: "Is it possible to locate the Nth file in a folder?"
date: 2009-12-29
forum: General Help
---

### Post by jiapei100 on 2009-12-29
Hi, all:

This might be an interesting question.

In one of my folder, there are loads of files which are named randomly but for sure, Ubuntu will sequence them alphabetically .

For example, if I just want to locate the 149th file in this folder and show its name, any command for that?
Or any script for it?

Cheers
JIA

---

### Post by MaxIBoy on 2009-12-29
Here's how I'd do it:
```
ls | head -n 149 | tail -n 1
```head -n 149 picks the first 149 off the list.
tail -n 1 picks the last off *that* list.

To store it in a variable:```
filename=`ls | head -n 149 | tail -n 1`
```Remember to use backticks instead of normal quotes!

---

### Post by dcstar on 2009-12-30
Is it assignment season already?

---

