---
title: "List files in a directory using Terminal?"
date: 2012-02-17
forum: General Help
---

### Post by PDA1 on 2012-02-17
Using Terminal, how do I list the files in a directory in chronological order?

The list must be in chronological order....and it would be nice if file sizes and dates could be included also.

I don't necessarily need the list created using Terminal...it's just the only way I thought it could be easily done.

Don't reply unless you know how to do it. 

Thanks.

---

### Post by winh8r on 2012-02-17
try


```
ls -l -t
```

---

### Post by drmrgd on 2012-02-17
I usually run:

```
ls -alrth
```

which lists all files ('a'), with long output ('l'), in reverse order so that the most recent is at the bottom ('r'), sorted by timestamp ('t'), in human readable size ('h').  

To make it easy, I have an alias in my .bashrc so that I just type 'lss' to give me this.  Run:

```
man ls
```

for more ls fun:D

---

### Post by PDA1 on 2012-02-17
Excellent!  Thank you all!

---

