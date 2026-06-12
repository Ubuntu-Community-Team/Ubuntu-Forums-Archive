---
title: "Ubuntu 10.04 Cache-Limit error (can't install sun-java6-jdk)"
date: 2012-08-02
forum: General Help
---

### Post by benjimenez805 on 2012-08-02
I am trying to install the HP developer sdk for the HP touchpad. On their site it states that I must use sun-java6.jdk because the java that comes with Ubuntu 10.04 does not work correctly with the SDK. So I added a source to the sources.list file on Ubuntu as the HP site stated, did the update and was being told that the package could not be found. So somewhere on the Internet I found another source for the package so I added that to the sources.list file. Now when I say to install the java6 package it starts to download and then I get this error message.

> Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing xfswitch-plugin (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.debian.org_debian_dists_squeeze_main_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.


I've tried to add more space to the 70debconf file, like this

> APT::Cache-Limit &#8220;10000000&#8243;; 

I still get the error. I saw on another site that I should use the open java version, but I don't know if this will work with the HP SDK. I will wait to hear from someone hear on what I should do. Thanks.

---

### Post by benjimenez805 on 2012-08-02
I found this fix on another site and it worked for me.

> $ sudo add-apt-repository ppa:ferramroberto/java
$ sudo apt-get update
$ sudo apt-get install sun-java6-jdk

---

### Post by Sandertje on 2012-08-02
I believe the Sun jdk is no longer supported for Ubuntu, because of license issues (in a nutshell: Oracle is being difficult). You will have to use the Openjdk these days.

See: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

