---
title: "script for each file in folder"
date: 2011-03-15
forum: General Help
---

### Post by mahmoodn on 2011-03-15
I want to do a specific task for each file in a specific directory. First I want to see if I can list them with:

```
#!/bin/bash
for filename in `pwd`
do
   echo $filename
done;

```

This the content of folder:
```
mahmood@pc1:test$ ls -l
total 4
-rw-r--r-- 1 mahmood mahmood  0 2011-03-15 20:13 a1.txt
-rw-r--r-- 1 mahmood mahmood  0 2011-03-15 20:13 a2.txt
-rw-r--r-- 1 mahmood mahmood  0 2011-03-15 20:13 a3.txt
-rwxr-xr-x 1 mahmood mahmood 62 2011-03-15 20:15 list.sh

```

but it doesn't work.
```
mahmood@pc1:test$ ./list.sh
/home/mahmood/test

```
Any idea about that?

---

### Post by sisco311 on 2011-03-15
Check out:
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

It's:
```
for file in *
do
  echo "$file"
done

```

---

### Post by TeoBigusGeekus on 2011-03-15
```
...for filename in `pwd`...
```

Try with 
```
#!/bin/bash
for filename in *
do
   echo $filename
done;
```

---

### Post by mahmoodn on 2011-03-15
Thanks :)

---

