---
title: "can't grab moblock packages natty noob"
date: 2011-09-02
forum: General Help
---

### Post by slummy on 2011-09-02
Heyo, I'm a noobuntu, so please be gentle. 

I'm trying to install moblock, following the process outlined here:
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

My issues:

1) Adding the repo:   sudo add-apt-repository ppa:jre-phoenix/ppa

--> Error reading [https://launchpad.net/api/1.0/~jrheonix/+archive/ppa:]("https://launchpad.net/api/1.0/%7Ejrheonix/+archive/ppa:") HTTP Error 404: Not Found

Adding the gpg key to the ring went fine, but


2) sudo apt-get update
--> W: Failed to fetch [http://ppa.launchpad.net/jre-pheonix/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/jre-pheonix/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/jre-pheonix/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/jre-pheonix/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.


3) sudo apt-get install moblock blockcontrol mobloquer
--> packages not found, of course. not got in 2) 

Help please, Owen

---

### Post by jre on 2011-09-04
> **slummy said:**
> --> Error reading [https://launchpad.net/api/1.0/~jrheonix/+archive/ppa:]("https://launchpad.net/api/1.0/%7Ejrheonix/+archive/ppa:") HTTP Error 404: Not Found
The "jrheonix" instead of jrephoenix might be the reason. Please check if you misspelled something. Just copy and paste it, instead of typing.

Generally it should work. Further I recommend to install pgld, pglcmd and pgl-gui instead. They are the official successors, and moblock packages will soon be updated to them automatically anyway.

---

