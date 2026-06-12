---
title: "Deleting Files using Terminal"
date: 2010-05-24
forum: General Help
---

### Post by desmith1944 on 2010-05-24
I am trying to delete some files using Terminal.
Below is a copy of the response I receive after the execution,

david@david-desktop:~$ sudo apt-get remove backup-02.05.2010

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package backup-02.05.2010

The file backup-02.05.2010 is located under my home directory.

After doing a search I think that I need to use CHMOD but I do not know the commands to use.

I tried to move this file to the trash using Dolphin but it says my trash has exceeded it limits but, their is nothing in the trash. The file size is approx. 1.7 gig.

I am using Ubuntu 2010 final i386 Gnome Desktop.

Thanks for the help.

---

### Post by DOSIX on 2010-05-24
remove as in deleting files:

sudo rm /mydirectory/myfile.file

for deleting a directory you have to let 'rm' know that it's recursive:

sudo rm -rf /mydirectory/

-r means recursive
-f means force

if deleting a directory, you must add the slash afterwords, if not you might screw it up. also, this doesn't move it to the trash, it permanently deletes the files/folders.

---

### Post by SlidingHorn on 2010-05-24
**Do NOT do this unless you're absolutely sure you want to get rid of this file**

```
sudo rm -f <filename>
```

the "-f" basically means: "do it, and don't give me any lip about it."  Keep your Ubuntu-Pimp hand strong, my friend

---

### Post by desmith1944 on 2010-05-24
DOSIX & SlidingHorn that did the job. I will put those commands in my memory bank for a later use.

---

### Post by Agent ME on 2010-05-24
If the file is owned by your user (which it probably is if it's in your home directory) then you don't need "sudo".

---

### Post by SlidingHorn on 2010-05-24
> **Agent ME said:**
> If the file is owned by your user (which it probably is if it's in your home directory) then you don't need "sudo".

+1 

Correct...no sense in giving yourself more power than needed.  Less chance of damaging your system that way, too.

---

### Post by desmith1944 on 2010-05-24
Thanks Agent Me I did not know that either. Another memory bank insert. Thanks.

---

### Post by blur xc on 2010-05-24
> **SlidingHorn said:**
> **Do NOT do this unless you're absolutely sure you want to get rid of this file**

```
sudo rm -f <filename>
```the "-f" basically means: "do it, and don't give me any lip about it."  Keep your Ubuntu-Pimp hand strong, my friend

yeah- be very careful...

sudo rm -rf is very dangerous.  I said this before, and I'll say it again- put the -rf flags AFTER your file path is entered and you know it's correct.
```
sudo rm /home/name/somedir/somefile -rf
```I do this from time to time- accidentally hit enter early...  If you only got so far as
```
sudo rm -rf /home<accidnetal enter>
```you just hosed yourself.  Accidentally deleting  some system direcotry and making your computer crash and be unbootable isn't that big of a deal*.  Just reinstall your os, you lose nothing except time.  Chances are the stuff that's in your home directory is harder or even impossible to replace.

BM

*edit- provided that you have your /home on a separate partition from your system directories.

---

### Post by nothingspecial on 2010-05-24
You do not need to use sudo if you own the file/directory.```


sudo rm -rf
```

is a very dangerous command and you can completely hose your system if you are in the wrong working directory, or make a typo.

For example, if you wanted to remove everything in ~/bin and didn`t realise that you were in / then ```
sudo rm -rf bin/*
``` would remove bash itself (amongst other vital utilities).

Similarly if you were in ~ and you typed ```
sudo rm -rf * .jpeg
``` (notice the space), you would remove the entire contents of your home directory.

I use it all the time, just make sure you don`t make a mistake ;)

---

