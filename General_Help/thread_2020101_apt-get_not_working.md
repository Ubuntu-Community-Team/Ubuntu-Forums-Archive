---
title: "apt-get not working"
date: 2012-07-07
forum: General Help
---

### Post by The_Eggert on 2012-07-07
Hello :)
I can't seem to get my apt-get command to work at the moment..
When I'm asked to run "apt-get -f install" to fix some unmet dependencies (or whatever it does - I just follow instructions :)), I am met with the following error message:
```

Me@MyComputer:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libncurses5-dev
Suggested packages:
  ncurses-doc
The following packages will be upgraded:
  libncurses5-dev
1 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
1 not fully installed or removed.
Need to get 0 B/222 kB of archives.
After this operation, 5,761 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of libncurses5-dev:
 libncurses5-dev depends on libncurses5 (= 5.7+20090803-2ubuntu3); however:
  Version of libncurses5 on system is 5.9-4.
dpkg: error processing libncurses5-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 libncurses5-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried to remove the package which seems to be causing problems (libncurses5-dev), but without any luck to do so..

Please help :P

---

### Post by jmfal on 2012-07-07
Try this first
```
   sudo dpkg --configure -a   
```

```
   sudo apt-get install -f  
```

Sometimes a app/package has to be installed completely before you can remove it

---

### Post by diesch on 2012-07-07
*apt-get* wants to install *libncurses5-dev* from Lucid but you have libncurses5 from Precise installed. There's something wrong with you package manger.

Which version of Ubuntu are you using? 
What does
```
apt-cache policy libncurses5-dev libncurses5
```
print?

---

### Post by The_Eggert on 2012-07-08
> **LinuxMaster007 said:**
> Have you installed any repositories lately other than the default repos that come with Ubuntu 12.04?

I have a few repos added, but they were all there, long before any problems began to show :)

> **jmfal said:**
> Try this first
```
   sudo dpkg --configure -a   
```

```
   sudo apt-get install -f  
```

Sometimes a app/package has to be installed completely before you can remove it

The first command runs without any output to the console, while the second command gives me the same error as before :(

> **diesch said:**
> *apt-get* wants to install *libncurses5-dev* from Lucid but you have libncurses5 from Precise installed. There's something wrong with you package manger.

Which version of Ubuntu are you using? 
What does
```
apt-cache policy libncurses5-dev libncurses5
```
print?

I'm running Ubuntu 12.04 (64-bit) :)
The command you mentioned, prints:
```

libncurses5-dev:
  Installed: 5.7+20090803-2ubuntu3
  Candidate: 5.9-4
  Version table:
     5.9-4 0
        500 http://dk.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
 *** 5.7+20090803-2ubuntu3 0
        100 /var/lib/dpkg/status
libncurses5:
  Installed: 5.9-4
  Candidate: 5.9-4
  Version table:
 *** 5.9-4 0
        500 http://dk.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

One thing that might be worth mentioning.. I just downloaded a .deb file for the library - It may well be, that I, being tired, have downloaded the wrong version without checking first..

---

### Post by The_Eggert on 2012-07-08
I think I fixed it now, by using the command:
```

sudo dpkg --force-all -r libncurses5-dev

```

Atleast now I can use apt-get again, so I'm marking the thread as solved.
If one of you clever guys sits, tearing your hair out, because of me just masking the problem, feel free to yell at me :P

But for now, thank you for replying :)

---

