---
title: "delete folders containing certain file type"
date: 2011-11-25
forum: General Help
---

### Post by mbeltoft on 2011-11-25
I have a big folder tree and I need to delete all folders containing a certain file type. 


can this be done with a command so i don't have to go through every folder to see if it have this filetype inside?

---

### Post by oldtimer7777 on 2011-11-25
Yes, you use the locate command to create a list of folders that contain that file, cut and paste that list to a script to batch del those directories..   I would just write a little bash script to handle this.

> **mbeltoft said:**
> I have a big folder tree and I need to delete all folders containing a certain file type. 


can this be done with a command so i don't have to go through every folder to see if it have this filetype inside?

---

### Post by Jacobonbuntu on 2011-11-25
> **mbeltoft said:**
> I have a big folder tree and I need to delete all folders containing a certain file type. 


can this be done with a command so i don't have to go through every folder to see if it have this filetype inside?

I would say, search the directory (from nautilus) for file extension and delete the found documents

edit: ah, I see you want to delete the *folders,* then my method won't work...
I should start reading better :)

---

### Post by mbeltoft on 2011-11-25
> **oldtimer7777 said:**
> Yes, you use the locate command to create a list of folders that contain that file, cut and paste that list to a script to batch del those directories..   I would just write a little bash script to handle this.

could you give an example as i have no idea how i should do this

---

### Post by Vaphell on 2011-11-25
so these directories are to be wiped out with everything they contain? 
```
while read f; do echo rm -rf "${f%/*}"; done < <( find "$PWD" -iname '*txt' -type f )
```
it will print out the list of commands, there will be duplicates but it doesn't matter. If you are sure everything is fine with the list, remove echo to perform rm. Testing on some sample data would be nice too because rm is not joking - if something goes wrong hello file recovery programs :)

---

### Post by mbeltoft on 2011-11-25
> **Vaphell said:**
> so these directories are to be wiped out with everything they contain? 
```
while read f; do echo rm -rf "${f%/*}"; done < <( find "$PWD" -iname '*txt' -type f )
```
it will print out the list of commands, there will be duplicates but it doesn't matter. If you are sure everything is fine with the list, remove echo to perform rm. Testing on some sample data would be nice too because rm is not joking - if something goes wrong hello file recovery programs :)

Worked perfect. tnx :D

---

