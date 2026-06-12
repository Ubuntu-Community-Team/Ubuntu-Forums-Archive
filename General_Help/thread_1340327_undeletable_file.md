---
title: "undeletable file"
date: 2009-11-28
forum: General Help
---

### Post by simartem on 2009-11-28
There is an undeletable file on a HDD on my network device. The device is a media consol and I reach the device on network.. The path is as follows :

```


smb://venus/hdd1/


```

There is an undeletable file on the HDD, and i dont know how to fix the problem.
I made chmod for the file (777), but it still is not deletable.

---

### Post by NoaHall on 2009-11-28
The path you gave is to the hard drive. You can't delete a hard drive.

---

### Post by simartem on 2009-11-28
hi, excuse me i didnt mean it.. I know its a HDD path. The file i am trying to delete is located at the following path :

```


smb://venus/hdd1/xx/hd dolby city redux.m2ts


```

When i try to delete the xx directory, it says "directory not empty"
When i am trying to delete "hd dolby city redux.m2ts", the operation seems complete but when i check the directory again, the file is there.

---

### Post by NoaHall on 2009-11-28
Well, you can't have gaps in the name.
Can you post which command you're using?

It should be something like -
```
 sudo rm -rf smb://venus/hdd1/xx/
```
or maybe
```
 sudo rm smb://venus/hdd1/xx/hd\ dolby\ city\ redux.m2ts
```

---

### Post by simartem on 2009-11-28
command line does not recognize the path as a source..
```

smb://venus/hdd1/xx/hd\ dolby\ city\ redux.m2ts

```

i guess there must have been some mounting points such as /media/disks/ but i dont know the correct location

---

### Post by sdowney717 on 2009-11-28
can you view this network location using nautilus?
if so, then right click and select mount. it will show up in the left panel. perhaps then you can get rid of it.

---

