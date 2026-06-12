---
title: "How to install tar.bz2 after extract"
date: 2009-11-22
forum: General Help
---

### Post by Alanbuntu on 2009-11-22
i already installed stardict but i also want to install stardict oxford dictionary(which is Eng-Trad Chinese), can anyone tell me how to do after this?

alanlinux@alanlinux:~/Documents$ tar xvfj stardict-oxford-big5-2.4.2.tar.bz2
stardict-oxford-big5-2.4.2/
stardict-oxford-big5-2.4.2/oxford-big5.dict.dz
stardict-oxford-big5-2.4.2/oxford-big5.idx
stardict-oxford-big5-2.4.2/oxford-big5.ifo

what command should i use next?

thanks for your help

---

### Post by jm2 on 2009-11-22
go into the star directory
cd star (whatever was listed above as I can't see it)

look for a readme file
ls 
look at that file for any special instructions for installing follow them if there are any.
cat readme | more (will list the file and stop at each page. press return for the next page)

If there isn't a readme or other instructions..

Usually the next step is to type these commands one at a time at the command line.


sudo ./configure
sudo make
sudo install

note: these may take a while to run or not.

---

### Post by Alanbuntu on 2009-11-23
> **jm2 said:**
> go into the star directory
cd star (whatever was listed above as I can't see it)

look for a readme file
..

how can i find out the star directory? thk u

---

### Post by Mr Nemo on 2009-11-23
Your probably gonna have to search a bit for it.

It looks like you tared it in /home/yourname/documents

sudo ./configure
sudo make
sudo make install

then you should be able to run it.

try searching for oxford

im fairly new to ubuntu so i hope this was of some help

---

### Post by audiomick on 2009-11-23
Hi. The star directory would presumably be the highest folder that was created by extracting the .tar file.
That is where you can expect to find information about the installation.

---

### Post by Mr Nemo on 2009-11-23
Audiomick has a good point, sometimes you dont need to compile after you extract from a .tar. Look for help files, INSTALL files or readme files.

---

### Post by Alanbuntu on 2009-11-23
there is no help file or readme file or install file. only files showed in my first thread. i tried to type sudo ./configure in the star directory but it returned the message like 'no such directory'

i just give up...so frustrating

---

### Post by jm2 on 2009-11-29
I did a google on install startdict here is alink of what to do next.

[http://ubuntuforums.org/archive/index.php/t-768440.html](http://ubuntuforums.org/archive/index.php/t-768440.html)

It says to do a move to a directory. As these have been compiled already.

---

