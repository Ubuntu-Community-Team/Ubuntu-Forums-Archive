---
title: "Can't find X11"
date: 2012-04-13
forum: General Help
---

### Post by HarryG123 on 2012-04-13
Continuation of post [http://ubuntuforums.org/showthread.php?p=11840224#post11840224](http://ubuntuforums.org/showthread.php?p=11840224#post11840224)

I tried the command[FONT=monospace]
[/FONT]```
sudo apt-get xlibs-dev
```[FONT=monospace]
[/FONT][FONT=monospace]but it doesn't work.

I'm running xubuntu 11.10

TYVM
[/FONT]

---

### Post by jocko on 2012-04-13
The command should be:
```
sudo apt-get **install** xlibs-dev
```But from the other thread I see that your problem is with installing fontforge.
Why not just get it from the repos with this command:
```
 sudo apt-get install fontforge
```Or find it in the software centre...

---

### Post by HarryG123 on 2012-04-13
Thank you Jocko.  Fontforge apparently doesn't reside in software repository. 

Downloading it manually, extracting it from the tarball, then running ./configure yields a the following warning:

```
 *******************************************************************
 * This version of fontforge will only run scripts. No X libraries *
 * (or X include files or some such) were found so there is NO user*
 * interface!!!!! If you want a UI try installing X11 on your      *
 * system.                                                         *
 * Caveat: You will probably need to install two packages, the     *
 *  base X11 package and the developer SDK package                 *
 *******************************************************************

```This is what I get when I try to install xlibs-dev
```
~$sudo apt-get install xlibs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xlibs-dev

```The problem remains...

I think I'll try synaptic again, and try installing the developer packages...

I'll post my results in this thread. Thanks for all your help.

---

### Post by raja.genupula on 2012-04-13
make sure that in software center sources all 11.10 sources are enabled .

---

