---
title: "Matlab cannot find JRE"
date: 2011-01-16
forum: General Help
---

### Post by layers on 2011-01-16
I am trying to install Matlab in 9.10 x86, but the installer gives me the following. I've tried as sudo, then with "install -glnx86", but it always gives me these lines. Can someone help me install it?

```
ibo@ibo-laptop:~/Desktop/MatLab R2010b [UNIX]$ ./install
dirname: missing operand
Try `dirname --help' for more information.
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /java/jre/glnx86/jre does not exist.
---------------------------------------------------------------------------

```

---

### Post by veggen on 2011-01-16
I know nothing of Matlab installation but it is obvoius it's looking for java in a place where there's no any. The only idea I can come up with is to see if you can somehow chnage the path it's looking at or make the /java/jre/glnx86/jre simlink to an actual java installation folder (probably /user/lib/jvm/<something>).

---

### Post by layers on 2011-01-16
You're right veggen, there isn't anything wrong with the installer (I've used the same files to install it on another machine). The whole folder is on the Desktop, and I don't know if it should be in ~ directory. 

The folder it is looking for is clearly there, and I did "chmod 777" it.
Does that change your opinion?
```
ibo@ibo-laptop:~$ cd Desktop/MatLab\ R2010b\ \[UNIX\]/
ibo@ibo-laptop:~/Desktop/MatLab R2010b [UNIX]$ cd java/jre/glnx86/jre
ibo@ibo-laptop:~/Desktop/MatLab R2010b [UNIX]/java/jre/glnx86/jre$ cd ~/Desktop/ibo@ibo-laptop:~/Desktop$ ls -l
total 62008
-rw-r--r-- 1 ibo ibo 63419938 2011-01-16 11:35 AdbeRdr9.4-1_i386linux_enu.deb
drwxrwxrwx 9 ibo ibo     4096 2011-01-15 11:49 MatLab R2010b [UNIX]
ibo@ibo-laptop:~/Desktop$ 
```

---

### Post by layers on 2011-01-16
anyone?

---

### Post by veggen on 2011-01-20
Hmm... The only thing I can come up with is that it's trying to find java in /java/jre/glnx86/jre instead of ./java/jre/glnx86/jre, i.e. starting from root and not the current folder. Just for the test I'd try creating a hierarchy it seems to looks for, and if the error message changes, that would be a clue.
Sorry I can't be of more help... but if it's of any consolation, you don't seem to be the only one with the problem. Check out some of the [top hits](http://www.google.com/search?client=opera&rls=en&q=The+directory+/java/jre/glnx86/jre+does+not+exist.&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest), there are some advices given that might help.

---

### Post by safaroth on 2011-06-04
> **layers said:**
> 

```
ibo@ibo-laptop:~/Desktop/MatLab R2010b [UNIX]$ ./install
dirname: missing operand
Try `dirname --help' for more information.
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /java/jre/glnx86/jre does not exist.
---------------------------------------------------------------------------

```

I had similar problem. Apparently, Matlab installation gives this error if the path to iso directory has spaces in it. Try mounting to \media\matlab. It should work

---

