---
title: "Creating a folder for each file in a directory"
date: 2011-06-04
forum: General Help
---

### Post by Ravenian on 2011-06-04
Hello,
I need to create a folder for every single file in a directory, possibly making the folder have the same name as the file that it will be containing. 
Is it possible to do via terminal?
Thanks!

---

### Post by jamesisin on 2011-06-04
Here is one possible method:

```
for i in *
do mkdir "$i"
done
```

You might prefer to use /the/actual/path instead of just an asterisk.

---

### Post by jamesisin on 2011-06-04
That won't catch hidden files (and it will capture folders as well but fail when it tries to create them).  FYI.

---

### Post by matt_symes on 2011-06-04
Hi

> **Ravenian said:**
>  possibly making the folder have the same name as the file that it will be containing. 

If the directory name is the same as the file name then no, because in Linux every thing is a file and you get a file name clash.

Here's an example.

```
matthew@matthew-laptop:~/a$ ls -l
total 4
-rw-r--r-- 1 matthew matthew 6 2011-06-04 17:48 a
matthew@matthew-laptop:~/a$ file a
a: ASCII text
matthew@matthew-laptop:~/a$ mkdir a
mkdir: cannot create directory `a': File exists
matthew@matthew-laptop:~/a$ 

```

You need to have a different folder name than the file name then that is achievable using the find with the -exec option.

Kind regards

---

### Post by Ravenian on 2011-06-04
I tried that command, but it says "cannot create directory: file exists"
Am I doing something wrong?

Exactly what Matt_symes said.
Could you explain the -exec option?

---

### Post by jamesisin on 2011-06-04
Oops.  My bad.  He's right.  Folders *are* files.  Try something like this:

```
for i in *
do mkdir "$i".FOLDER
done
```

---

### Post by Ravenian on 2011-06-04
That succeeded in creating the folders! I forgot to mention that it would also be nifty to automatically move each file in its respective folder, is that possible? If not, I'll just move them manually.

---

### Post by jamesisin on 2011-06-04
Add something like this after the mkdir and before the done:

```
mv "$i" "$i".FOLDER
```

You may have to adjust matters if you are using the /full/paths.

---

### Post by Ravenian on 2011-06-04
That did the trick. Thank you so much!

---

### Post by matt_symes on 2011-06-04
Hi

Here's a one line find command that will create a directory called _<file_name> and move the file called <file_name> into it.

```
find * -type f -exec  mkdir _'{}' \; -exec  mv '{}' _'{}' \;
```This will recurse all the way down  the tree so if you need to stop try using the -maxdepth switch. _This is important to understand._

Have a look at this.

```
matthew@matthew-laptop:~/a$ ls -l
total 4
-rw-r--r-- 1 matthew matthew 6 2011-06-04 17:48 a
matthew@matthew-laptop:~/a$ find * -type f -exec  mkdir _'{}' \; -exec  mv '{}' _'{}' \;
matthew@matthew-laptop:~/a$ ls -l
total 4
drwxr-xr-x 2 matthew matthew 4096 2011-06-04 18:05 _a
matthew@matthew-laptop:~/a$ ls -l _a
total 4
-rw-r--r-- 1 matthew matthew 6 2011-06-04 17:48 a
matthew@matthew-laptop:~/a$
```Kind regards

---

### Post by Telengard C64 on 2011-06-04
```
foo$ ls
adduser.conf  wodim.conf  wvdial.conf
foo$ find -maxdepth 1 -type f | while read ; do mkdir "${REPLY}.FOLDER" && mv "$REPLY" "${REPLY}.FOLDER" ; done
foo$ ls -R
.:
adduser.conf.FOLDER  wodim.conf.FOLDER  wvdial.conf.FOLDER

./adduser.conf.FOLDER:
adduser.conf

./wodim.conf.FOLDER:
wodim.conf

./wvdial.conf.FOLDER:
wvdial.conf
foo$
```

---

