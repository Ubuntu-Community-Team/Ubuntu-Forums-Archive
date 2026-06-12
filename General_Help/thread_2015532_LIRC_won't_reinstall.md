---
title: "LIRC won't reinstall"
date: 2012-07-03
forum: General Help
---

### Post by Zac280 on 2012-07-03
I just did a clean install of 12.04 and MythTV, followed by installing iguanaIR and compiling it into the LIRC source following these instructions:

[http://iguanaworks.net/2012/compile-lirc-into-deb-package/](http://iguanaworks.net/2012/compile-lirc-into-deb-package/)

IR blaster was working just fine, like I had it on 10.04, but then I stupidly let Ubuntu update and it broke. I've tried apt-get remove lirc and apt-get install lirc, but it produces 

```
htpc@htpc:~$ sudo apt-get install lirc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  lirc-x
The following NEW packages will be installed:
  lirc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/615 kB of archives.
After this operation, 2,908 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package lirc.
(Reading database ... 178471 files and directories currently installed.)
Unpacking lirc (from .../lirc_0.9.0-0ubuntu1_i386.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up lirc (0.9.0-0ubuntu1) ...
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 20
Errors were encountered while processing:
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can compile the source, and it will look like the iguanaIR is included when I do 

```
lircd -H '?'
```

But when I use irsend I get

```
irsend: hardware does not support sending
```

which makes me think the driver isn't really installed. I used the setup instructions for iguanaIR [here]("http://iguanaworks.net/projects/IguanaIR/wiki/GettingStarted"), and the iguanaIR commands work, just not the LIRC commands.

---

### Post by Zac280 on 2012-07-03
I finally got the driver compiled into the LIRC source and my IR blaster is working now. The problem now is LIRC still hangs from the apt-get install, and is preventing me from installing anything else.

I've tried apt-get clean and apt-get update, then dpkg --configure -a and apt-get install -f

```
htpc@htpc:/etc$ sudo dpkg --configure -a
Setting up lirc (0.9.0-0ubuntu1) ...
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 128
Errors were encountered while processing:
 lirc

```

```
htpc@htpc:/etc$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up lirc (0.9.0-0ubuntu1) ...
dpkg: error processing lirc (--configure):
 subprocess installed post-installation script returned error exit status 128
Errors were encountered while processing:
 lirc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm prevented from installing anything else because of this so it's a major issue I can't seem to work around.

---

