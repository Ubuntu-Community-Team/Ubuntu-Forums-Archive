---
title: "How to install NMIS v8 on Ubuntu 11.04"
date: 2011-09-18
forum: General Help
---

### Post by nseries on 2011-09-18
HI guys,

I'm totally new to Ubuntu and new to this NMIS (Network Management Information System) from Opmantek. Below is the link to the source:
[http://opmantek.com/](http://opmantek.com/)

Basically the files i download is in tar.gz, which i know it needs to extract to somewhere into a directory to proceed for installation. Can i use the Ubuntu Software center for this installation? I hope someone can provide step by step to guide here.

I need this NMIS working for my office, to monitor my network equipment up time and monitoring the health as well. 

Hope and help and really appreciate. 

Thanks!

---

### Post by Bodsda on 2011-09-18
> **nseries said:**
> HI guys,

I'm totally new to Ubuntu and new to this NMIS (Network Management Information System) from Opmantek. Below is the link to the source:
[http://opmantek.com/](http://opmantek.com/)

Basically the files i download is in tar.gz, which i know it needs to extract to somewhere into a directory to proceed for installation. Can i use the Ubuntu Software center for this installation? I hope someone can provide step by step to guide here.

I need this NMIS working for my office, to monitor my network equipment up time and monitoring the health as well. 

Hope and help and really appreciate. 

Thanks!

Are you stuck on a particular step?

The usual steps for compiling source code are as follows

1) Install required packages (build-essential for example)
2) Extract source
3) 'cd' into source directory
4) Read the README
5) Run ./configure
6) Run make
7) Run sudo make install 

Further reading: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Hope this helps,
Bodsda

---

### Post by kesi on 2012-02-27
Hi,

I found the reference to the NMIS8 installation instructions in the README of the tarball, the link is at [http://www.opmantek.com/Docs]("http://www.opmantek.com/Docs")

I also found some excellent Ubuntu specific documentation in a blog @
[http://showbrain.blogspot.com.au/2011/07/installing-nmis-network-management.html]("http://showbrain.blogspot.com.au/2011/07/installing-nmis-network-management.html")

I hope that helps.


Kesi

---

