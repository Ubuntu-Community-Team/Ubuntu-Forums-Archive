---
title: "permission denied?"
date: 2011-01-15
forum: General Help
---

### Post by garyed on 2011-01-15
I have a couple files that I try to delete but I get "permission denied".
Logically I assumed they were owned by root but they were not, they were owned by me(gary). I could easily delete them using sudo but I can't figure out why I can't just as user: gary.  I could even chmod them as user gary & change their permissions as so:
```
chmod 777 id_rsa
```
so I have full permissions but I could still not delete the file without using sudo in front of the rm command. 
Can anyone explain?

---

### Post by sikander3786 on 2011-01-15
Did you take a look at the output of

```
ls -l
```

Please post the output if you can't figure it out yourself :-)

---

### Post by sisco311 on 2011-01-15
In order to delete a file you must have write permission on the file's parent _directory_ and execute permission on the directory, the directory's parent, and all ancestor directories up to and including "/" (root).

See: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by garyed on 2011-01-15
> **sisco311 said:**
> In order to delete a file you must have write permission on the file's parent _directory_ and execute permission on the directory, the directory's parent, and all ancestor directories up to and including "/" (root).

See: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
That was the problem. Even though the file had permission for me to remove, the directory "/home" where the file resided was owned by root. Evidently if the file resides in a subdirectory under /home like /home/gary then it can be deleted by the user & doesn't have to be root.

---

