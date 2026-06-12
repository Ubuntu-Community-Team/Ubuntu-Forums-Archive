---
title: "Find out what OS ur using 32bit or 64bit"
date: 2009-10-28
forum: General Help
---

### Post by Vigh on 2009-10-28
Just a quick question how do I find out which version of buntu im using. I was having difficulty installing the 9.10 rc, so ive installed 9.04 off of a linux magazine cd, but im not sure if ive got 32-bit or 64-bit, and appear to be having some trouble installing adobe flash, cheers Ant

---

### Post by sahabcse on 2009-10-28
Run the below command terminal

uname -a

its showing i686 GNU/Linux - 32 bit
or x86_64 - 64 bit

---

### Post by prshah on 2009-10-28
> **Vigh said:**
> im not sure if ive got 32-bit or 64-bit, 

The Terminal (Applications-Accessories-Terminal) command 
```
uname -m
```  will give you: i686 - 32 bit or x86_64 - 64 bit.

---

