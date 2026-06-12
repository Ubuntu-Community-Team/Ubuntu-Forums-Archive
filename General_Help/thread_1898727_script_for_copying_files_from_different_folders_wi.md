---
title: "script for copying files from different folders with same name"
date: 2011-12-22
forum: General Help
---

### Post by publicjo on 2011-12-22
Dear all,

I have three different files, all named toto.txt, located in three different folders 
/jojo/mask/aa10000
/jojo/mask/bb10003
/jojo/mask/cc10005

I would like to copy them in these folders
/baba/all/aa10000
/baba/all/bb10003
/baba/all/cc10005

(copying the toto.txt located in /jojo/mask/aa10000 to /baba/all/aa10000 and so on....)

Could you help me to write a script which could do this ??

thanks very much !
publicjo

---

### Post by claracc on 2011-12-22
You can use command cp in console (xterm):

cp ./jojo/mask/* ./baba/all/ (only the three specified files in it?).

If there are more than the three specified files ( aa1000, bb1003, cc1005), you can copy them one by one:

cp ./jojo/mask/aa1000 ./baba/all/ , I am assuming that directories /jojo/ and /baba/ are under your personal folder

Any case, there will be for sure more efficient ways (more experienced users in console's command will tell), you can see the man for cp command: man cp

---

### Post by Telengard C64 on 2011-12-22
```
#! /bin/bash

for i in "aa10000" "bb10003" "cc10005"
do
    cp "/jojo/mask/$i/toto.txt" "/baba/all/$i/"
done
```

---

