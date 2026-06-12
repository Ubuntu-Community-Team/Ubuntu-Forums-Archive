---
title: "VM ubuntu - apt-get install xxx =&gt; Couldn't find package xxx"
date: 2010-05-13
forum: General Help
---

### Post by rsginmansavior on 2010-05-13
On my VirtualBox running Redhat 5 => 
#uname -a 
Linux 2.6.18-194.3.1.el5 #1 SMP Sun May 2 04:17:42 EDT 2010 x86_64  x86_64 x86_64 GNU/Linux

After installing apt-get, I can't install sun-java6-jdk, aptitude, etc. Your help is very appreciated.

# apt-get update
Reading Package Lists... Done
Building Dependency Tree... Done

# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 removed and 0 not upgraded.

# apt-get install sun-java6-jdk
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package sun-java6-jdk

# apt-get install aptitude
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package aptitude

My /etc/apt/sources.list.d/os.lis =>
# Name: Operating system and updates

### Red Hat Enterprise Linux
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/os
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/updates
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/os
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/updates
#rpm [http://yam](http://yam) rhel$(VERSION)as-$(ARCH) os updates
#rpm [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt os updates

### Fedora Core Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/core
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH) core updates

### Red Hat Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/os
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH) os updates

---

### Post by sandyd on 2010-05-13
> **rsginmansavior said:**
> On my VirtualBox running Redhat 5 => 
#uname -a 
Linux 2.6.18-194.3.1.el5 #1 SMP Sun May 2 04:17:42 EDT 2010 x86_64  x86_64 x86_64 GNU/Linux

After installing apt-get, I can't install sun-java6-jdk, aptitude, etc. Your help is very appreciated.

# apt-get update
Reading Package Lists... Done
Building Dependency Tree... Done

# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 removed and 0 not upgraded.

# apt-get install sun-java6-jdk
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package sun-java6-jdk

# apt-get install aptitude
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package aptitude

My /etc/apt/sources.list.d/os.lis =>
# Name: Operating system and updates

### Red Hat Enterprise Linux
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/os
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/updates
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/os
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/updates
#rpm [http://yam](http://yam) rhel$(VERSION)as-$(ARCH) os updates
#rpm [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt os updates

### Fedora Core Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/core
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH) core updates

### Red Hat Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/os
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH) os updates

apt-get is for debs (debian based), while rpm is for red hat based distros. 
Its not a good idea to mix them.

---

### Post by rsginmansavior on 2010-05-14
> **carlee said:**
> apt-get is for debs (debian based), while rpm is for red hat based distros. 
Its not a good idea to mix them.
Thanks. I can't install it from yum as listed below either. Should I download it from Sun Java site directly?
# yum install sun-java6-jdk
Loaded plugins: rhnplugin, security
Setting up Install Process
No package sun-java6-jdk available.
Nothing to do

---

### Post by rsginmansavior on 2010-05-14
> **carlee said:**
> apt-get is for debs (debian based), while rpm is for red hat based distros. 
Its not a good idea to mix them.

Following steps posted at [http://blogs.gurulabs.com/dax/2009/03/64bit-java-appl-1.html](http://blogs.gurulabs.com/dax/2009/03/64bit-java-appl-1.html) works.


[LIST=1]
[*]Back on your 64bit system run: **yum install java-1.6.0-sun java-1.6.0-sun-plugin.x86_64**     On  a 32bit system run: **yum install java-1.6.0-sun java-1.6.0-sun-plugin**
[*]Optionally, if you want the JDK and not just the JRE (because you  plan on compiling Java software), then run: **yum install java-1.6.0-sun-devel**
[/LIST]

---

### Post by dcstar on 2010-05-14
> **rsginmansavior said:**
> On my VirtualBox running Redhat 5 => 
........

This is a forum specifically for support questions Ubuntu based distros, **not** for anything else.

---

### Post by rsginmansavior on 2010-05-17
> **carlee said:**
> apt-get is for debs (debian based), while rpm is for red hat based distros. 
Its not a good idea to mix them. Carol - your response is useful and have a very nice day. - ss

---

### Post by tyoli on 2010-07-28
> **rsginmansavior said:**
> On my VirtualBox running Redhat 5 => 
#uname -a 
Linux 2.6.18-194.3.1.el5 #1 SMP Sun May 2 04:17:42 EDT 2010 x86_64  x86_64 x86_64 GNU/Linux

After installing apt-get, I can't install sun-java6-jdk, aptitude, etc. Your help is very appreciated.

# apt-get update
Reading Package Lists... Done
Building Dependency Tree... Done

# apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 removed and 0 not upgraded.

# apt-get install sun-java6-jdk
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package sun-java6-jdk

# apt-get install aptitude
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package aptitude

My /etc/apt/sources.list.d/os.lis =>
# Name: Operating system and updates

### Red Hat Enterprise Linux
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/os
#repomd [http://yam](http://yam) rhel$(VERSION)as-$(ARCH)/updates
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/os
#repomd [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt/updates
#rpm [http://yam](http://yam) rhel$(VERSION)as-$(ARCH) os updates
#rpm [http://mirror.centos.org](http://mirror.centos.org) centos/$(VERSION)/apt os updates

### Fedora Core Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/core
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) fedora/linux/$(VERSION)/$(ARCH) core updates

### Red Hat Linux
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/os
#repomd [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH)/updates
#rpm [http://ayo.freshrpms.net](http://ayo.freshrpms.net) redhat/$(VERSION)/$(ARCH) os updates

hi maybe this is too late, i had the same problen with ubuntu 10.04 and i did most of what you did and in the end it's just a problem of wrong name you must enter:
apt-get install openjdk-6-jre

and that's worked for me.

---

