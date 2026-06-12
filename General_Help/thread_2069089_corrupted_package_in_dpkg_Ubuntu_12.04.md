---
title: "corrupted package in dpkg Ubuntu 12.04"
date: 2012-10-10
forum: General Help
---

### Post by ThethundarBird on 2012-10-10
I installed ```
ppa:webupd8team/java
``` and I get the following error

Output from:
```
sudo apt-get install oracle-java7-installer
```
```

Reading package lists...
Done Building dependency tree        
Reading state information... Done
Suggested packages:   binfmt-support visualvm ttf-baekmuk ttf-unfonts
ttf-unfonts-core   ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho   ttf-arphic-uming The following
packages will be upgraded:   oracle-java7-installer 1 upgraded, 0
newly installed, 0 to remove and 0 not upgraded. 1 not fully installed
or removed. Need to get 0 B/16.0 kB of archives. After this operation,
64.5 kB of additional disk space will be used. 
Could not exec dpkg! E: Sub-process /usr/bin/dpkg returned an error code (100)
```

i did afterwords those line of code trying to resolve the issue becuase it is not existed actually in the /usr/bin/dpkg there is no dpkg

```
mkdir /tmp/dpkg
cd /tmp/dpkg
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
sudo cp ./usr/bin/dpkg /usr/bin/
sudo apt-get update
sudo apt-get install --reinstall dpkg
```

then i get this
```

$     sudo apt-get install --reinstall dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,814 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: warning: 'dpkg-deb' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
```
How can I fix this?

---

### Post by drpjkurian on 2012-10-10
Open a terminal and type following commands
first enter as root
```
sudo -i
```
enter your sudo command

2.move to your bin/usr
```
 cd /usr/bin
```

3. make it executable
> chmod 777 dpkg

4. update the system
```
apt-get update
```

---

### Post by Lars Noodén on 2012-10-10
> **drpjkurian said:**
> 3. make it executable
Quote:
chmod 777 dpkg

That makes the program world-writable, which is quite dangerous.  The permissions for /usr/bin/dpkg should be 755.

---

