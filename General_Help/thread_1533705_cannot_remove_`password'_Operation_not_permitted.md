---
title: "cannot remove `password': Operation not permitted"
date: 2010-07-18
forum: General Help
---

### Post by adit on 2010-07-18
I have a file named password in my home directory.  I want to delete it.
```
:~$ rm password
rm: cannot remove `password': Operation not permitted
``````
:~$ ls -l password
-rw-r--r-- 1 adit adit 8 2010-06-29 10:00 password

```This is my home directory.  I am the owner of this file.  Still I can not delete this file.

---

### Post by sisco311 on 2010-07-18
To delete a file you need write permission for the directory where the file is stored and execute access to all parent directories back to the root.

Also check the attributes of the file:
```
lsattr password
```

---

### Post by Vishnu V on 2010-07-18
Check the attribute of the file by
```

 sudo lsattr password
```
if it has attribute a or i remove it by
```
 sudo chattr -ai password
```

---

### Post by adit on 2010-07-18
```
:~$ lsattr password 
-----a-----------e- password
```I have read, write and execute permissions for the directory which contains this file.

---

### Post by adit on 2010-07-18
```
sudo chattr -ai password
```The above code worked.  I deleted the file successfully.

---

