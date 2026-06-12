---
title: "[Emergency]I Can'T install  Any soft Ubuntu !2.04 LTS"
date: 2012-05-02
forum: General Help
---

### Post by Raihan004 on 2012-05-02
hi i got a trouble. Today i setup ubuntu 12.04 Lts. But I Cant setup any soft from Ubuntu SOf Center Or Using Terminal Can Any One Help ME please .

When I want to Setup any Soft From Soft Cnerter Here A option Use This source . But Cant setup from this source . also cant install from terminal  

raihan@raihan-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'vlc' has no installation candidate

pls help me..

---

### Post by whatthefunk on 2012-05-02
In a terminal run:
```
sudo apt-get update
```

After doing this you should be able to find your packages.

---

### Post by kc1di on 2012-05-02
> **whatthefunk said:**
> In a terminal run:
```
sudo apt-get update
```

After doing this you should be able to find your packages.

if this does not work try typing this in a terminal:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```
Copy and past them one line at a time in your terminal
good luck,
D ;)

---

### Post by Raihan004 on 2012-05-02
> **kc1di said:**
> if this does not work try typing this in a terminal:

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update
```
Copy and past them one line at a time in your terminal
good luck,
D ;)

when i comand sudo apt-get update some file is missing their. . What ever why i can't install soft directly from soft manager like as previous version?

---

### Post by whatthefunk on 2012-05-02
> **Raihan004 said:**
> when i comand sudo apt-get update some file is missing their. . What ever why i can't install soft directly from soft manager like as previous version?

What file is missing??

You should be able to install from the software manager, but you need to update the software sources first.  Have you updated since you installed??

---

### Post by Raihan004 on 2012-05-02
> **whatthefunk said:**
> What file is missing??

You should be able to install from the software manager, but you need to update the software sources first.  Have you updated since you installed??

after complete instally, i update from update manager.

---

### Post by kc1di on 2012-05-02
Go to software center then click on edit at top bar then on Software Sources. make sure all the boxes have a check mark in them on the Ubuntu software tab. 

Then in a terminal to the ```
sudo apt-get update
``` again.

VLC is in the repositories and should be able to be installed.
If this does not work please post the out put of your terminal when you run sudo apt-get update

---

### Post by TBABill on 2012-05-02
Did you check your software sources to be sure you didn't remove it from being available?

---

