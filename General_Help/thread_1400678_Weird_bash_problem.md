---
title: "Weird bash problem ?"
date: 2010-02-07
forum: General Help
---

### Post by mohitchawla on 2010-02-07
Hi, I am trying to run an executable file from a directory in a terminal, but it just won't happen. This is really strange:

```
alcy@alcy-desktop:~$ cd mprime
alcy@alcy-desktop:~/mprime$ ls -l
total 4156
-rw-r--r-- 1 alcy alcy    2110 2009-03-16 20:52 license.txt
-rwxr-xr-x 1 alcy alcy 4140905 2009-03-16 20:52 mprime
-rw-r--r-- 1 alcy alcy   23062 2009-03-16 20:52 readme.txt
-rw-r--r-- 1 alcy alcy    6860 2009-03-16 20:52 stress.txt
-rw-r--r-- 1 alcy alcy   19768 2009-03-16 20:52 undoc.txt
-rw-r--r-- 1 alcy alcy   53776 2009-03-16 20:52 whatsnew.txt
alcy@alcy-desktop:~/mprime$ ./mprime
bash: ./mprime: No such file or directory
alcy@alcy-desktop:~/mprime$ sudo ./mprime
sudo: unable to execute ./mprime: No such file or directory
alcy@alcy-desktop:~/mprime$ 




```

What's going on here, please help. I have tried running other such executables, same error.

---

### Post by MooPi on 2010-02-07
Check to see if your running the proper mprime. 64bit versus 32bit ?

---

### Post by gmargo on 2010-02-07
When you ask a question like this, it is probably best to specify what the software is and where you got it from.  Fortunately, google quickly told me you are probably running [SIZE=2]"[/SIZE][FONT=Tahoma][SIZE=5][SIZE=2]Great Internet Mersenne Prime Search" software from [/SIZE][/SIZE][/FONT][FONT=Tahoma][SIZE=5][SIZE=2][http://www.mersenne.org/freesoft]("http://ubuntuforums.org//http://www.mersenne.org/freesoft/") and that the downloaded software is specifically [http://mersenneforum.org/gimps/mprime259.tar.gz](http://mersenneforum.org/gimps/mprime259.tar.gz)[/SIZE][/SIZE][/FONT]**[FONT=Tahoma][SIZE=5][SIZE=2].[/SIZE][/SIZE][/FONT]**[FONT=Tahoma][SIZE=5][SIZE=2] This is 32-bit software and I was able to run it on both Hardy and Karmic, both 32-bit.

If you are running 64-bit, there's a 64-bit choice: [http://mersenneforum.org/gimps/mprime259-linux64.tar.gz](http://mersenneforum.org/gimps/mprime259-linux64.tar.gz)

[/SIZE][/SIZE][/FONT][FONT=Tahoma][SIZE=5][SIZE=2]You can check to see if you have all the required libraries by running "ldd mprime" to see the libraries it is linked to.[/SIZE][/SIZE][/FONT]

---

### Post by rnerwein on 2010-02-07
hi
please post the output of: file mprime
and ldd mprime

ciao

---

### Post by DGortze380 on 2010-02-07
```

sudo chmod+x mprime 

```

Then try again.

---

