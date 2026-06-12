---
title: "Please help"
date: 2010-10-24
forum: General Help
---

### Post by kevinls on 2010-10-24
[This is for Ubuntu 9.04]

I followed the instructions from this page:  [http://adammichaelroach.com/blog/050...-jackalope-904]("http://adammichaelroach.com/blog/050409-wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904")

Scroll down and you'll find a section called "Updating Punkbuster." My problem occurred with the code:  sudo chmod +x pbweb.x8               

[QUOTE="**text taken from (above) website**"]                                     
[I]**Updating Punkbuster**
 
Finally, we can update Punkbuster.  This is a multi-step process, but  I  assure you if you follow these instructions, it will work just fine.    In the terminal:
 
cd /usr/local/games/enemy-territory/pb/htm/
sudo wget [http://www.evenbalance.com/downloads/cod2/pbsecsv.htm](http://www.evenbalance.com/downloads/cod2/pbsecsv.htm)
cd ..
_**sudo chmod +x pbweb.x86**_
sudo ./pbweb.x86[/I]
                      [/QUOTE]           
After I pasted that line of text into a terminal it gave me this output:

[quote="**terminal** **output**"]*chmod: cannot access `pbweb.x86': No such file or directory*[/quote]

So, what should I do?  Btw, I need precise step by step instructions or else I won't know what to do.

Thanks!

---

### Post by gunsten on 2010-10-24
Either something went wrong with the download (wget) or you're in the wrong directory (not the same as the script file you want to execute).

Use *dir* (list content in the current directory), and *cd* to change directory, or just have a look at the directory with the file manager (I mean *places *in the main menu).

---

### Post by wojox on 2010-10-24
Open your terminal and 

```
cd /usr/local/games/enemy-territory/pb/htm/
```

To see what's in there

```
ls -al
```

---

### Post by kevinls on 2010-10-24
```
total 2624
drwxr-xr-x 2 root root    4096 2010-10-23 22:57 .
drwxr-xr-x 3 root root    4096 2010-10-23 00:39 ..
-rw-r--r-- 1 root root   46541 2010-10-23 00:35 la001347.htm
-rw-r--r-- 1 root root  655956 2010-10-23 00:35 lc001152.htm
-rw-r--r-- 1 root root 1113258 2010-10-23 00:35 ls001149.htm
-rw-r--r-- 1 root root   66640 2010-10-23 00:35 ma001347.htm
-rw-r--r-- 1 root root  275182 2010-10-23 00:35 mc001152.htm
-rw-r--r-- 1 root root    1418 2009-12-10 16:02 pbsecsv.htm
-rw-r--r-- 1 root root    1418 2009-12-10 16:02 pbsecsv.htm.1
-rw-r--r-- 1 root root    1418 2009-12-10 16:02 pbsecsv.htm.2
-rw-r--r-- 1 root root   79213 2010-10-23 00:35 wa001347.htm
-rw-r--r-- 1 root root  385305 2010-10-23 00:35 wc001152.htm
```

---

### Post by wojox on 2010-10-24
According to [Evenbalance]("http://www.evenbalance.com/downloads/cod2/pbsecsv.htm") those files should be downloaded to your /pb directory, not /htm

---

### Post by kevinls on 2010-10-27
So how do I download those files to my /pb directory?

---

### Post by kevinls on 2010-10-30
I still need help.

---

### Post by bobwyajnr on 2010-10-30
Hi OP


```
sudo cp /usr/local/games/enemy-territory/pb/htm/* /usr/local/games/enemy-territory/pb/
```

Should move your files. BTW **cp** (Unix BASH shell command 'copy') has a switch **-r** to move subdirectories recursively as well.

Please could you choose a more appropriate title for this thread. **How to install Punkbuster for Quake: Enemy Territory?**? would have been more descriptive!!

**wget** just downloads file from a URL to the present working directory (which you can check by typing **pwd** - present working directory).

When following the original instructions did you actually type:
```
cd ..
```
That would change your working directory from:
*/usr/local/games/enemy-territory/pb/htm/*
to:
*/usr/local/games/enemy-territory/pb/*

In UNIX (and Windows actually) the file **..** is an alias for parent directory (of the present working directory).
The file **.** is an alias for present working directory.

Bob

---

### Post by kevinls on 2010-10-30
Thanks.

It works now.

---

### Post by bobwyajnr on 2010-10-31
> **kevinls said:**
> Thanks.

It works now.

Can you mark this thread as solved (using *your* **thread tools** at the top of the thread in your browser). Just start another thread (with an appropriate title [-X ) if you have further problems...

Bob :)

---

