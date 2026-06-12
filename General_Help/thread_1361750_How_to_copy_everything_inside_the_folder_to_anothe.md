---
title: "How to copy everything inside the folder to another folder"
date: 2009-12-22
forum: General Help
---

### Post by klnyc on 2009-12-22
Hello there, 

    Basic stuff, I know how to copy folder to another folder.
But, how do you copy everything inside the folder to another folder with command line?

Yes, sorry about this super newbie question. I just started with Linux few weeks ago.

---

### Post by dasy2k1 on 2009-12-22
either from in the folder

```
cp ./* <PATH TO DESTINATION>
```

or if the destination folder dosent exist yet you can from the directory where you can see the folder

```
cp -r <foldername> <newfolder path>
```


eg to copy the folder foo to one called bar in the directory above i could do

```
 cp -r ./foo ../bar
```

---

### Post by lewisforlife on 2009-12-22
```
cp -r /path/to/first/directory/* /path/to/second/directory
```

---

### Post by klnyc on 2009-12-22
> **dasy2k1 said:**
> either from in the folder

```
cp ./* <PATH TO DESTINATION>
```

or if the destination folder dosent exist yet you can from the directory where you can see the folder

```
cp -r <foldername> <newfolder path>
```


eg to copy the folder foo to one called bar in the directory above i could do

```
 cp -r ./foo ../bar
```

  Thank you!

---

### Post by dasy2k1 on 2009-12-22
for information, 

the -r flag applies to most of the common commands (cp, mv, rm) etc 

and stands for recursivly, 
ie do this to a directory and all its contents.

so ```
mv -r foo bar
``` renames the directory foo to bar and keeps all its contents (actually moves foo to bar with all its contents but that has the same effect) 


also you might want to hit the mark thread as solved tag to help other people here!

---

