---
title: "synaptic help ubuntu 9.10"
date: 2009-11-14
forum: General Help
---

### Post by muscularsage on 2009-11-14
hi! i came across this site ([http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/](http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/)) whose basic idea was to accelerate apt-get downloads using accelerators such as axel,prozilla. there were some tar archives given i tried to compile them, i did not know bout them but tried in the terminal.....and after that am not able to use synaptic itself! when i try to download it says "unknown failure 32512" can some one help me throwing some light on this?thanks in  advance.

---

### Post by muscularsage on 2009-11-17
can some one kindly help guys! i cannot install even a single software!

---

### Post by muscularsage on 2009-11-20
can anyone kindly help!

---

### Post by Scunnered on 2009-11-20
It looks very much like the obvious reply is start everything over again.  Do a conplete fresh install of 9.10 and apply a little patience.  It is not as if synaptic downloads are slow and it is imperative that everything is done at the speed of light.

---

### Post by P4man on 2009-11-20
That link doesnt work, so Im unsure what you did, but it was probably a bad idea :)

Anyway, what happens when you open a terminal and type

```
sudo apt-get update
```

I assume it wont work but Id like to see the error. Also try

```
sudo aptitude update
```


If apt-get is broken perhaps aptitude still works and can be used to reinstall apt-get.

---

### Post by muscularsage on 2009-11-20
am gettin the same error even while using aptitude

---

### Post by muscularsage on 2009-11-20
this is more info:
fron that page i downloaded apt.tar.gz
then i triedthis 
ajay@ajay-laptop:~/Downloads/apt$ ./configure
bash: ./configure: No such file or directory
ajay@ajay-laptop:~/Downloads/apt$ 
then i hit
ajay@ajay-laptop:~/Downloads/apt$ make
g++ http.cc -o http
sudo rm /usr/lib/apt/methods/http
[sudo] password for ajay: 
sudo cp http /usr/lib/apt/methods/

and this is wat it shows 
then when i tried to apt-get update it showed faild and shows unknown failure 32512
i guess this will help

---

### Post by P4man on 2009-11-20
so you messed up apt :S

You could try this:

```
sudo dpkg-reconfigure apt
```

But I doubt that will fix it. Since you deleted the http method, you could try downloading this file:
[http://www.mediafire.com/?zkzeag4jldz](http://www.mediafire.com/?zkzeag4jldz)

and copy it to /usr/lib/apt/
You will need root permission to do that, so if you,re not usre how to do that press alt F2 and type

```
gksudo nautilus
```

us that to copy the downloaded file.

And please next time dont try stuff like that. You tried compiling a different apt version (which sounds like a very bad idea), the compile failed, yet you continue with the command deleting parts of apt and not being able to replace them with the newly compiled one...

---

### Post by muscularsage on 2009-11-21
hello thanks 4 ur interest in solving ma problem.........tis gettin screwed worse........i followed ur instructions and it remained unsolved so i copied that http file to a folder in that path called methods and replaced an existing file named  http and now tis showin this when i tried to reload in synaptic:

Method http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctlyMethod http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctlyMethod http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctlyMethod http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctlyMethod http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctlyMethod http has died unexpectedly!Sub-process http returned an error code (100)Method /usr/lib/apt/methods/http did not start correctly

---

### Post by P4man on 2009-11-21
Last idea. Grab apt from here:
[http://packages.ubuntu.com/karmic/apt](http://packages.ubuntu.com/karmic/apt)
download and try installing it.

If that fails, I guess you're looking at a new install..

---

### Post by muscularsage on 2009-11-21
u mean reinstallling ubuntu?

---

### Post by muscularsage on 2009-11-21
got synaptic workin after reinstall of apt! tis workin !thanks P4MAN THANKS A LOT i mean it!

---

### Post by JBAlaska on 2009-11-21
If you want to speed up your synaptic downloads, choose a faster mirror. You can do this in software sources, download from, other, select best server

---

