---
title: "sudo in LTS"
date: 2010-06-05
forum: General Help
---

### Post by deeppow on 2010-06-05
Just installed the newer version of Ubuntu, i.e. LTS.  Have used Ubuntu in the past so I'm somewhat familiar with its use.  This time when I try 

sudo "some application" it says it can find the command

or

su "some application" it says authorization failed

Has something changed or do I have something screwed up?


Thanks.:P

---

### Post by Leppie on 2010-06-05
is the application you're trying to run with sudo installed on your system?
for instance, gparted is an application included on the livecd but has to be installed once you finish installing the system if you want to use it.
try sudo with other commands, like:
```
sudo mount -l
```
this should list all mounted partitions.

---

### Post by sisco311 on 2010-06-05
sudo resets the PATH environment variable to /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin (directories are separated by a colon [noparse](:))[/noparse]

If the command is not in one of those directories you have to specify the full or relative path to it. e.g. if the command is in the current working directory:
```
sudo ./command
```
or
```
sudo /path/to/dir/command
```

---

### Post by deeppow on 2010-06-05
Thanks folks, forgot the "./"   I always think it should know to look in the current location.

---

### Post by sisco311 on 2010-06-05
> **deeppow said:**
> Thanks folks, forgot the "./"   I always think it should know to look in the current location.

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

