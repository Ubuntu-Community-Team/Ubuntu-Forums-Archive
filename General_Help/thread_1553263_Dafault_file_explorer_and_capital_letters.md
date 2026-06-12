---
title: "Dafault file explorer and capital letters"
date: 2010-08-14
forum: General Help
---

### Post by RB_ on 2010-08-14
Is there a way to have the default 10.04 file explorer ignore capitals?

eg: If i have the files

BOB_1
BOB_2
BOB_3
bob_4
bob_5
bob_6

Ubuntu by default lists them in order starting with the lowercase letters 4-6, followed by the upper-case letters 1-3. I want them to be displayed in the order listed above. 

If this isn't possible, can I rename every single file in a folder to be made up of only caps?

Appreciated

RB_

---

### Post by x1a4 on 2010-08-14
Hi,

Which file system are you using?  If ext3, there's a tool [here]("http://bill.herrin.us/freebies/") which you can use.  To batch rename files search the repositories for 'rename'.  One tool I like to use is 'gprename'.  Try them all and see which one you like best.

---

### Post by chopinhauer on 2010-08-14
> **x1a4 said:**
> 
Which file system are you using?  If ext3, there's a tool [here]("http://bill.herrin.us/freebies/") which you can use.


A case insensitive file system is an abomination in the UNIX world. I can imaging hundreds of things that can break.

The shell is also a very fast way to batch rename files. For example:
```

cd /path/to/your/files && for i in bob*; do mv "$i" $(echo "$i"|tr [:lower:] [:upper:]); done

```
will capitalize you bob files.

---

### Post by chopinhauer on 2010-08-14
> **RB_ said:**
> 
Ubuntu by default lists them in order starting with the lowercase letters 4-6, followed by the upper-case letters 1-3. I want them to be displayed in the order listed above. 


It depends upon your language settings. What does the command
```

locale

```
give you? Except the "C" locale all the other collate in a case insensitive way.

---

