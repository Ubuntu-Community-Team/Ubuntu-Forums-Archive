---
title: "new system, cannot compile anything even though make is present"
date: 2011-08-14
forum: General Help
---

### Post by gleemer on 2011-08-14
I just installed a new Ubuntu Studio 11.04 system at home yesterday. It was relatively painless at first but now I'm trying to compile some of the programs that I built the system for and

```
./make
```simply is not working (returns command not found error). A makefile is present in both of the directories I'm working on. 

```
man make
```works perfectly fine. apt-get install insists that make is present, it also insists that gcc and build-essential are present. Just for the heck of it I reinstalled build-essential but nothing changed. I hesitate to uninstall it or or uninstall make as I have several packages which depend on these and several more which recommend them.

I first got into Linux with Ubuntu Server 10.04 and I remember not being able to compile then but that was because I didn't have gcc or build-essential installed. Once I installed those packages everything was happy. Every google search I perform leads me either to "install build-essentiall / gcc" or to nothing at all. Thoughts on where I can go from here?

---

### Post by sum1nil on 2011-08-14
'./make' is looking for the command in the current directory and it is doubtful it exists.

'make' will use the make command from /usr/bin .

To configure the software you would use './configure', since configure is in the local directory.

Hope this helps.

---

### Post by Kira_Belka on 2011-08-14
Hi!.. 1. What do you want to compile? 2. right syntax .. simply make or make install when you built) but all depends from rules in make file)

---

### Post by gleemer on 2011-08-14
Well its been a long weekend I guess. And  I haven't been using Linux much lately. In any event plain "make" without the ./ works just fine. Thanks. Marking as solved.

---

