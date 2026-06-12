---
title: "root can't change permissions"
date: 2011-08-04
forum: General Help
---

### Post by jhargis1012 on 2011-08-04
Hello.

I'm new to Linux, and I've been learning how to use permissions. I ran into a weird problem in which I am unable to change permissions as root. I have a file I've been testing commands on, and somewhere along the line I think I gave it zero permissions. Now I'd like to restore some permissions, but can't. Here's what I'm looking at:

```
jeremy@jeremy-laptop:~/test$ ls -l
total 16
-rw-r--r-- 1 jeremy jeremy 235 2011-05-17 13:15 onelink
-rwxr-xr-x 1 jeremy jeremy  27 2011-08-02 18:05 threecopy
-rwxr-xr-x 1 jeremy jeremy  27 2011-05-09 17:10 three.txt
---------- 1 root   jeremy  19 2011-05-09 17:15 two
jeremy@jeremy-laptop:~/test$ sudo chmod 777 two
chmod: changing permissions of `two': Operation not permitted
jeremy@jeremy-laptop:~/test$ sudo chown jeremy two
chown: changing ownership of `two': Operation not permitted
jeremy@jeremy-laptop:~/test$ sudo chmod a+x two
chmod: changing permissions of `two': Operation not permitted
jeremy@jeremy-laptop:~/test$ 

```

I appreciate your help.

---

### Post by jerome1232 on 2011-08-04
On my system changing a files permissions to nothing doesn't hinder changing them again. It must be something else wrong. What filesystem are these files on? Can you change the permissions on the other files in that directory? Anything wonky with the parent folders permissions?

---

### Post by mixmaster on 2011-08-04
Is it possible that you have also screwed up the permissions of the test directory?  It may be that root no longer has the right to change files in that directory.  Back up (cd ..) and see what permissions test has.  If they are anything other than 777 change them and try again.

---

### Post by jhargis1012 on 2011-08-04
The files are all on an ext4 partition.

The permission on the folder seem normal.

```
drwxr-xr-x  2 jeremy jeremy   4096 2011-08-04 13:42 test

```

What's interesting is that I can change permissions just fine on two of the files in the directory ("onelink" and "threecopy"). I set them to 000 and then back up to 777 with no problems. On the other hand, the remaining two files are both denying me the permission change. How strange is that!

```
jeremy@jeremy-laptop:~/test$ ls -l
total 16
---------- 1 jeremy jeremy 235 2011-05-17 13:15 onelink
-rwxrwxrwx 1 jeremy jeremy  27 2011-08-02 18:05 threecopy
-rwxr-xr-x 1 jeremy jeremy  27 2011-05-09 17:10 three.txt
---------- 1 root   jeremy  19 2011-05-09 17:15 two

```

---

### Post by psusi on 2011-08-04
What do you get from lsattr two?

---

### Post by jhargis1012 on 2011-08-04
> **psusi said:**
> What do you get from lsattr two?

Ha! That was it. I had the "i" flag on both those files. I must've added it some time ago and forgotten about it since. I took the flag off, and it all works just fine. I was able to chmod "two". :) Thanks for the help!

---

### Post by afrodeity on 2012-02-05
have a similar problem with a directory containing files saved from testdisk. They all listed as owned by root, but chmod -R 777 does'nt' work. gksudo nautilus also no working on the files.

```

-rwxrwxrwx 1 root root   4910679 2009-05-01 15:07 Remix.pdf

```

---

