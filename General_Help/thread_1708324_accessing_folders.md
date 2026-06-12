---
title: "accessing folders"
date: 2011-03-16
forum: General Help
---

### Post by Hartfield on 2011-03-16
Hello, 

I am trying to access a folder through the terminal but I am not sure how. 

For example, I can access the documents by typing cd Documents.  BUT I do not know how I can access a folder that for example has a long name like: scangearm-mp-250series-1.60-1deb.tar.gz


thank you

---

### Post by WorMzy on 2011-03-16
That's not a folder, that's an archive. You can list it's contents with
```
tar -tzf scangearm-mp-250series-1.60-1deb.tar.gz
```

Or extract the contents with

```
tar -xzvf scangearm-mp-250series-1.60-1deb.tar.gz
```

---

### Post by TeoBigusGeekus on 2011-03-16
> **Hartfield said:**
> scangearm-mp-250series-1.60-1deb.tar.gz

This isn't a folder, it's an archive.
All you need to do is extract it
```
tar xvf scangearm-mp-250series-1.60-1deb.tar.gz
```

---

### Post by steaksauce on 2011-03-16
> **Hartfield said:**
> Hello, 

I am trying to access a folder through the terminal but I am not sure how. 

For example, I can access the documents by typing cd Documents.  BUT I do not know how I can access a folder that for example has a long name like: scangearm-mp-250series-1.60-1deb.tar.gz


thank you

That's true about it being an archive file (like a zip file)

But for folder access you can use
```
pwd
```
This will show you the current directory you are in

```
ls
```
This will show you the files and folders in the current directory you're in
```
cd (directory path)
```
This will change your working directory (the directory you're in) to another one.

For example:
```
steaksauce@korh-lnx-lptp:~$ pwd
/home/steaksauce
steaksauce@korh-lnx-lptp:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
steaksauce@korh-lnx-lptp:~$ cd /home/steaksauce/Downloads
steaksauce@korh-lnx-lptp:~/Downloads$ 

```

The files and directories are case sensitive. "Downloads" is different from "downloads"

---

### Post by steaksauce on 2011-03-16
Oh, the TAB key can be pressed to finish long file names. Say you want to run the code ```
tar xvf scangearm-mp-250series-1.60-1deb.tar.gz
```

Instead of typing all of the file name out you could type

```
 tar xvf scan
```
and press TAB and it would finish the rest of the filename for you
;)

---

