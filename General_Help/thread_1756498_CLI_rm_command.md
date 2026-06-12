---
title: "CLI rm command?"
date: 2011-05-12
forum: General Help
---

### Post by CVGH on 2011-05-12
Is there a way to remove all files that have the text 500804
in their filenames?
I did a restore and now I've got these scattered all through my file system in /etc /home and /var.

Thanks,

Brian

---

### Post by TeoBigusGeekus on 2011-05-12
```
find / -iname "*500804*" -exec rm "{}" \;
```
Replace / with the path in which you want the 500804 files removed. Running it as it is, will search your whole filesystem and delete them all.

---

### Post by Tanasqui on 2011-05-12
As an alternative to TeoBigusGeekus' suggestion you might consider :

```
mkdir movedfiles/; for file in $(locate "*500804*"); do mv $file movedfiles/;echo $file>>moverecord; done;
```

This line will create a directory called movedfiles, find all of the files containing 500804 then move each one to that directory while making note of the original location of each record in a file called moverecord, in case you break something (a required file could possibly have 500804 in the name)

This is just a safer option, it makes it possible to restore the files.

---

### Post by TeoBigusGeekus on 2011-05-12
> **Tanasqui said:**
> 
This is just a safer option, it makes it possible to restore the files.

Agreed.
Code:
```
find / -iname "*500804*" -exec mv "{}" movedfiles/ \;
```

---

### Post by Tanasqui on 2011-05-12
> **TeoBigusGeekus said:**
> Agreed.
Code:
```
find / -iname "*500804*" -exec mv "{}" movedfiles/ \;
```

But this wont create a list of original file locations will it?

---

### Post by matt_symes on 2011-05-12
Hi

If you are going to go with post #3 then remember to type

```
sudo updatedb
```before running the command to update your database in case it's out of date.

Kind regards

---

### Post by CVGH on 2011-05-12
> **Tanasqui said:**
> As an alternative to TeoBigusGeekus' suggestion you might consider :

```
mkdir movedfiles/; for file in $(locate "*500804*"); do mv $file movedfiles/;echo $file>>moverecord; done;
```This line will create a directory called movedfiles, find all of the files containing 500804 then move each one to that directory while making note of the original location of each record in a file called moverecord, in case you break something (a required file could possibly have 500804 in the name)

This is just a safer option, it makes it possible to restore the files.

Had some "Permission denied" issues running as "sudo", so did sudo su and it ran like a champ!! 


Many thanks folks!! 

Brian

---

