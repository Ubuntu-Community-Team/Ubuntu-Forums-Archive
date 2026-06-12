---
title: "blkid is not showing exfat format partition"
date: 2011-09-21
forum: General Help
---

### Post by masuch on 2011-09-21
Hi,

I do not see exfat partition when I use blkid command. Is there any trick how to fix it ? ( fdisk shows it)

thanks for help.

---

### Post by raja.genupula on 2011-09-21
Hey man , i got this .
[http://code.google.com/p/exfat/wiki/QuckStartGuide](http://code.google.com/p/exfat/wiki/QuckStartGuide)

all the best .

---

### Post by masuch on 2011-09-22
> **raja.genupula said:**
> Hey man , i got this .
[http://code.google.com/p/exfat/wiki/QuckStartGuide](http://code.google.com/p/exfat/wiki/QuckStartGuide)

all the best .

Thanks , I believe it works, but I was not successful with compilation of utils-linux version 2.19.1 because of segmentation fault in "lomount.c" - so I have to solve it firstly if I am able to.

---

### Post by masuch on 2011-09-22
> **raja.genupula said:**
> Hey man , i got this .
[http://code.google.com/p/exfat/wiki/QuckStartGuide](http://code.google.com/p/exfat/wiki/QuckStartGuide)

all the best .

After couple of compilation errors I finally install util-linux_2.19.1-2ubuntu3.tar.gz. I had to solve segmentation fault and run sudo make instead of make command because of some permission problems. I am not sure if I can do it but more or less it works - less because I have to usually restart twice ubuntu instance to make it to login. (I can not get login screen - just black screen - it behaves similar when I have got into problem if catalyst driver is not properly installed)
  I have noticed that there is already 2.20 version which I am going to try later when I can get to [http://userweb.kernel.org/~kzak/util-linux/](http://userweb.kernel.org/~kzak/util-linux/).
  I have noticed some other discrepancies - like disk mounter in gnome 2 shows only mounted disks, ... .

---

### Post by raja.genupula on 2011-09-22
Hey man 

actually this the process  installing from a tar
```
./configure
make
sudo make install
```

remember these things for the next time & one more thing is each source pkg have a readme file and its consists of installation process also . so please read it once to get the process of installation.

all the best .

---

### Post by masuch on 2011-09-23
> **raja.genupula said:**
> Hey man 

actually this the process  installing from a tar
```
./configure
make
sudo make install
```

remember these things for the next time & one more thing is each source pkg have a readme file and its consists of installation process also . so please read it once to get the process of installation.

all the best .

Hi man,
You missed probably my last post. So again, I had to run "sudo make" (NOT sudo make install) - what surprised me. I have always read readme file from source package when I am going to compile any source "tar". I have mentioned that installation process was not as easy as you described: ./configure && make && sudo make install because of many compilation discrepancies - some of them I mentioned. And thread has been already closed couple of hours before you post it.
So, what about is your last post ???

---

