---
title: "VirtualBox dependencies, help!"
date: 2010-02-11
forum: General Help
---

### Post by ktat on 2010-02-11
Hi, I've recently installed Karmic Koala (64 bit version) on my pc via a live cd.

I still can't get my epson scanner to work so my plan was to get VirtualBox and then run xp inside Karmic.

My problem is that my pc doesn't have an internet connection.  After downloading the VB software from my library I went home to install - unfortunately I got the following error message:

> Error: Dependency is not satisfiable: libqt4-network (>= 4.5.1)

What now, I imagine there's a solution for this??

---

### Post by zvacet on 2010-02-12
Download all packages marked with red ball and on the bottom of the page download package for your architecture.Put all packages in one folder and put that folder in your Ubuntu home directory.Just for example let say that folder name is simply folder.From terminal

```
cd folder
sudo dpkg -i *deb
```

That will install all dependencies and package.You can find package and dependencies [here.]("http://packages.ubuntu.com/karmic/libqt4-network")

---

### Post by ktat on 2010-02-14
ta, I'll give this a try - I am wondering though do I also need to download the dependecies for the dependencies? ie, qt4 depends on libc6 which depends on findutils which depends on... etc.

This could be a lengthy process..

---

### Post by ktat on 2010-02-16
I tried installing dependencies as suggested here is the output:
```

xxxx@xxxx-karmic:~$ cd qt4 
xxxx@xxxx-karmic:~/qt4$ sudo dpkg -i *deb 
[sudo] password for xxxx: 
(Reading database ... 113487 files and directories currently installed.) 
Preparing to replace libc6 2.10.1-0ubuntu15 (using libc6_2.10.1-0ubuntu15_amd64.deb) ... 
Unpacking replacement libc6 ... 
Preparing to replace libgcc1 1:4.4.1-4ubuntu8 (using libgcc1_4.4.1-4ubuntu8_amd64.deb) ... 
Unpacking replacement libgcc1 ... 
Preparing to replace libqt4-network 4.5.3really4.5.2-0ubuntu1 (using libqt4-network_4.5.3really4.5.2-0ubuntu1_amd64.deb) ... 
Unpacking replacement libqt4-network ... 
Preparing to replace libqtcore4 4.5.3really4.5.2-0ubuntu1 (using libqtcore4_4.5.3really4.5.2-0ubuntu1_amd64.deb) ... 
Unpacking replacement libqtcore4 ... 
Preparing to replace libstdc++6 4.4.1-4ubuntu8 (using libstdc++6_4.4.1-4ubuntu8_amd64.deb) ... 
Unpacking replacement libstdc++6 ... 
Preparing to replace zlib1g 1:1.2.3.3.dfsg-13ubuntu3 (using zlib1g_1.2.3.3.dfsg-13ubuntu3_amd64.deb) ... 
Unpacking replacement zlib1g ... 
Setting up libc6 (2.10.1-0ubuntu15) ... 

Setting up libgcc1 (1:4.4.1-4ubuntu8) ... 

Setting up libstdc++6 (4.4.1-4ubuntu8) ... 

Setting up zlib1g (1:1.2.3.3.dfsg-13ubuntu3) ... 

Setting up libqtcore4 (4.5.3really4.5.2-0ubuntu1) ... 

Setting up libqt4-network (4.5.3really4.5.2-0ubuntu1) ... 

Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
xxxx@xxxx-karmic:~/qt4$ 
```

Looks like it went alright to me, however, when I attempt to install VB I still get the same error message.

---

