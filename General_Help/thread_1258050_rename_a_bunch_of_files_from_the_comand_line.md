---
title: "rename a bunch of files from the comand line"
date: 2009-09-04
forum: General Help
---

### Post by blur xc on 2009-09-04
I tried renaming a bunch of files at the command line last night and ran into some errors, and I don't know what I was doing wrong.

For example, say I have some files test1, test2, test3, etc... and I want to rename all of them to be *.txt.  In dos I could simply enter rename *.* *.txt and be done...  I tried something similar in the terminal "mv *.txt *.bak" and it told me that *.bak was not a directory.  I couldn't figure it out.  

Any help?

Thanks,
BM

---

### Post by DaithiF on 2009-09-04
try the 'rename' command
```
man rename
```

for your example, 
```
rename 's/$/.txt/' *
```

---

### Post by blur xc on 2009-09-04
> **DaithiF said:**
> try the 'rename' command
```
man rename
```for your example, 
```
rename 's/$/.txt/' *
```


Crazy- how come all the cli books say to use the mv command to rename a file?  I've read like three of them so far...(maybe not all the way through...)

That's a bit frustrating.

thanks for the 411.

BM

---

### Post by DaithiF on 2009-09-04
mv for renaming files one at a time, rename for batch renaming.

---

### Post by hangfire on 2009-09-04
> **blur xc said:**
> I tried renaming a bunch of files at the command line last night and ran into some errors, and I don't know what I was doing wrong.

For example, say I have some files test1, test2, test3, etc... and I want to rename all of them to be *.txt.  In dos I could simply enter rename *.* *.txt and be done...  I tried something similar in the terminal "mv *.txt *.bak" and it told me that *.bak was not a directory.  I couldn't figure it out.  

Any help?

Thanks,
BM

```
for FILE in test*
do
   mv "${FILE}" "${FILE}".txt
done
```


-HF

---

