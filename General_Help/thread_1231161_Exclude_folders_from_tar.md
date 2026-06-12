---
title: "Exclude folders from tar"
date: 2009-08-04
forum: General Help
---

### Post by dragos2 on 2009-08-04
How to exclude list of folders from tar ?

---

### Post by nikhilk on 2009-08-04
> **dragos2 said:**
> How to exclude list of folders from tar ?

From tar's man page
> 
--exclude=PATTERN
              exclude files, given as a PATTERN


e.g. to exclude all log files from a folder
```
tar czvf test.tar test1.txt test1.txt --exclude *.log
```

---

### Post by dragos2 on 2009-08-05
> **nikhilk said:**
> From tar's man page


e.g. to exclude all log files from a folder
```
tar czvf test.tar test1.txt test1.txt --exclude *.log
```

I read the manual, thanks for the example but I mean how to exclude for example
/folder1 and /folder2 and /folder3 using --exclude ?

---

### Post by nhanquy on 2009-08-05
```

tar cf - -C /home/<yourdir>/test --exclude test1 --exclude test2 . | tar xvf - -C /home/<yourdir>/newtest

```means move all sub dir from dir test to newtest but not subdir test1 and test2

---

### Post by nikhilk on 2009-08-05
> **dragos2 said:**
> I read the manual, thanks for the example but I mean how to exclude for example
/folder1 and /folder2 and /folder3 using --exclude ?

You can use the --exclude switch to exclude directories as well (after all in Linux, a directory is also a file, albeit of a special type).
e.g. you want to tar the directory ~/tar_me_up and it contains folder1, folder2 and folder3 that you don't want to include in the tar-ball, run
```
tar czvf test.tar.gz ~/tar_me_up --exclude folder1 --exclude folder2 --exclude folder3
```

---

### Post by dragos2 on 2009-08-05
Thanks :)

---

