---
title: "Can't install FreeNX server on 10.10"
date: 2010-10-17
forum: General Help
---

### Post by davidbr on 2010-10-17
I followed the instructions at [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) to install the FreeNX server on 10.10, including the manual download of [https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz](https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz).

Here is where I get stuck:
```
 
$ sudo /usr/lib/nx/nxsetup --install
------> It is recommended that you use the NoMachine key for
easier setup. If you answer "y", FreeNX creates a custom
KeyPair and expects you to setup your clients manually.
"N" is default and uses the NoMachine key for installation.
Do you want to use your own custom KeyPair? [y/N] 
/usr/lib/nx/nxsetup: line 140: .: filename argument required
.: usage: . filename [arguments]
Setting up  ...mkdir: missing operand 
Try `mkdir --help' for more information.  
```

---

### Post by flyboy69 on 2010-10-18
I have the same problem, anyone find a solution yet?

SOLVED:
 Installing the FreeNX server on Ubuntu Maverick Meerkat (10.10) - [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by davidbr on 2010-10-19
No. I had to use NoMachine NX server instead.

---

### Post by vranjan on 2010-10-19
I had freeNX installed on ubuntu 10.04... however, it stopped working on 10.10... since then I have not been able to reinstall it. Would appreciate any help.

---

### Post by iserlohn on 2010-10-20
I followed the instructions and used the Jaunty repos instead of the Lucid ones and it worked, otherwise, the client will always fail to connect...

---

### Post by yawnbox on 2010-11-05
Those instructions wasted half an hour.

Went here for the DEB files:
[http://www.nomachine.com/download-package.php?Prod_Id=2069](http://www.nomachine.com/download-package.php?Prod_Id=2069)

Downloaded Client, Node, and Server to Downloads folder on the 'server'

cd ./Downloads
sudo apt-get install libaudiofile0
sudo dpkg -i nxclient_3.4.0-7_i386.deb
sudo dpkg -i nxnode_3.4.0-14_i386.deb
sudo dpkg -i nxserver_3.4.0-14_i386.deb

and then same for the client but without the node and server

cheers

---

### Post by venik212 on 2010-11-08
I did the very same thing when my NX, which I had used for years, all of a sudden prevented me from logging into my Ubuntu 10.10 64 bit system.  It did not cure the problem-- I am still getting an error message about a server configuration error.  I did not reconfigure the server (how does one do that, anyway), so I am lost.
========================================

SOLVED: my .Xauthority file was corrupted.  I deleted it and rebooted, and all is well.

---

