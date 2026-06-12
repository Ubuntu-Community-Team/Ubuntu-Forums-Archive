---
title: "Install Python 3.1.1"
date: 2009-11-09
forum: General Help
---

### Post by mem0rex on 2009-11-09
I am trying to install Python 3.1.1 , I downloaded the tar file and extracted it with:

```
tar -xzf Python-3.1.1.tgz 

```Ok that worked fine, so I went to the Python directory and and ran: 

```
sudo ./configure

```And I get the following error: 

```
mem0rex@mem0rex-desktop:~/Desktop/Python-3.1.1$ sudo ./configure
checking for --with-universal-archs... 32-bit
checking MACHDEP... linux2
checking machine type as reported by uname -m... i686
checking for --without-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```Can someone please help me with this problem?
- Thanks

---

### Post by mem0rex on 2009-11-09
Anyone?

---

### Post by Mike'sHardLinux on 2009-11-09
Hi.

I don't know what version of Ubuntu you are running, but I am running Karmic and Python 3.1.1 is in the repos (universe).

---

### Post by mem0rex on 2009-11-09
I have 2.5 preinstalled, but I would like a more up to date version. And how do I access the Idle sell in python 2.5?

---

### Post by falconindy on 2009-11-09
If your only reason to install Python 3.1 is that you feel you need a more "up to date" version of Python, then you don't need it. That's really not how programming languages work. Release 2.6 is currently used by the overriding majority of Python apps and there's currently very little need or support for 3.x.

---

### Post by mem0rex on 2009-11-09
Ok well how do I use the IDLE shell in Python?

---

