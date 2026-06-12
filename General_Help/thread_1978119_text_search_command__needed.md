---
title: "text search command  needed"
date: 2012-05-11
forum: General Help
---

### Post by winzip on 2012-05-11
I want to search  a text  in  **XML files.**  I tried this ....

```
find /home/user/ -type f -exec grep -l "Netherlands" {} \;
```But this searches ALL  files.

What is the correct command to search  text  in XML files  ?

---

### Post by WorMzy on 2012-05-11
Look in find's man page for -name or -iname, those will do what you've described.

---

### Post by codemaniac on 2012-05-11
> **winzip said:**
> I want to search  a text  in  **XML files.**  I tried this ....

```
find /home/user/ -type f -exec grep -l "Netherlands" {} \;
```But this searches ALL  files.

What is the correct command to search  text  in XML files  ?

```
find /home/user/ -name "*.xml" -type f -exec grep -l "Netherlands" {} \;
```
The above would grep through only xml files .

---

### Post by Vaphell on 2012-05-11
grep can be made recursive so you don't need find for that

```
grep -r --include='*.txt' 'Netherlands' /home/user
```

---

### Post by codemaniac on 2012-05-11
> **Vaphell said:**
> grep can be made recursive so you don't need find for that

```
grep -r --include='*.txt' 'Netherlands' /home/user
```

Yes , another way around .Thanks Vaphell for pointing out the recursive feature of grep .

---

### Post by winzip on 2012-05-11
> **Vaphell said:**
> grep can be made recursive so you don't need find for that

```
grep -r --include='*.txt' 'Netherlands' /home/user
```

does  it  search  sub-folders  under    /home/user ?

---

### Post by Vaphell on 2012-05-11
-r makes grep recursive so it behaves just like find and checks the whole dir subtree of the picked dir
if you ran it, you'd know already :-)

---

