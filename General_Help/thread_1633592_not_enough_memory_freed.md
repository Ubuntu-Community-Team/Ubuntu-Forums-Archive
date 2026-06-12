---
title: "not enough memory freed"
date: 2010-11-29
forum: General Help
---

### Post by c2tarun on 2010-11-29
hi friends
i install gtypist and it displayed that something around 1MB will be downloaded and around 4MB space will be used.
but when i removed it by "sudo apt-get remove gtypist" it displayed that only around 2MB space will be freed. although 2MBs are negligible but still i just wanted to know where are my 2MBs.

---

### Post by aeiah on 2010-11-29
perhaps additional libraries are being held, or perhaps a lot of documentation and user files are being kept behind. does apt-get mention anything about certain packages no longer being needed? (it'll suggest running apt-get autoremove)

---

### Post by Spyderkid on 2010-11-29
Use this peice of code to remove the file/directory

(you need to go to the right directory first)

```
 shred --remove -n 10 -v (File Name) 
```

Also if you want to make sure you remove all bits of the file/program/directory from the RAM SWAP and physical memory use this...

```
srm -v ../(File Name) 
``` 

Hope thats of some help

---

### Post by c2tarun on 2010-11-30
it worked thanx :)

---

