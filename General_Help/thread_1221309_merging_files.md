---
title: "merging files"
date: 2009-07-23
forum: General Help
---

### Post by xgitboxx on 2009-07-23
im i have to merge about 42 .txt files into one big .txt
they go by the names "Wordlist00, Wordlist01 ect."  
they are in a folder on my desktop labeled "werdz"
how would i go about merging these

---

### Post by DGortze380 on 2009-07-23
[http://ubuntuforums.org/showthread.php?t=1210488](http://ubuntuforums.org/showthread.php?t=1210488)

---

### Post by ibutho on 2009-07-23
You could use a for loop e.g. 
```
for i in `ls`; do cat "$i" >> myfile;done
```
You may have to tinker with the loop to suite your needs.

---

### Post by michy99 on 2009-07-23
```
cd ~/Desktop/werdz
cat Wordlist* > BigWordlist
```

---

### Post by xgitboxx on 2009-07-23
i try to do what that thread says but it comes up as no file or directory found

---

### Post by xgitboxx on 2009-07-23
[IMG]http://tinypic.com/r/111ujk6/3[/IMG] =[ [IMG]http://i27.tinypic.com/111ujk6.png[/IMG]

---

### Post by ajgreeny on 2009-07-23
Linux is case sensitive so the command will be ```
cat WordList* > BigWordList
```Note the uppercase W & L.

---

