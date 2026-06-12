---
title: "How to get OpenJDK 7?"
date: 2011-03-06
forum: General Help
---

### Post by ukbeast on 2011-03-06
What is the difference between 6 and 7 and how to get the repository for Ubuntu 10.10?

---

### Post by lykeion on 2011-03-06
Lots of changes, see this: [http://en.wikipedia.org/wiki/Java_version_history#Java_SE_7.0](http://en.wikipedia.org/wiki/Java_version_history#Java_SE_7.0)

I don't think there's a Ubuntu repository for it but you can download a binary installer from the Oracle site. However if you're a regular user (not a developer) there's no need to install it yet.

---

### Post by ac90b671 on 2011-09-07
OpenJDK isn't the same as the Oracle Java JDK on the Oracle website.It's the open source implementation of the java virtual machine as promised by Sun. OpenJDK 7 is slated for 11.10 but you can add the OpenJDK ppa to get 7 on 11.04. 
```

sudo add-apt-repository ppa:dlecan/openjdk
sudo apt-get update
sudo apt-get install openjdk-7

```

---

### Post by GrzesiekC on 2011-12-18
> **ac90b671 said:**
> OpenJDK isn't the same as the Oracle Java JDK on the Oracle website.It's the open source implementation of the java virtual machine as promised by Sun. OpenJDK 7 is slated for 11.10 but you can add the OpenJDK ppa to get 7 on 11.04. 
```

sudo add-apt-repository ppa:dlecan/openjdk
sudo apt-get update
sudo apt-get install openjdk-7

```

Hi,

this PPA does not work in Natty. Is there any other ppa for it.

Cheers
Grzesiek

---

### Post by glitchsys on 2012-02-22
> **GrzesiekC said:**
> Hi,

this PPA does not work in Natty. Is there any other ppa for it.

Cheers
Grzesiek

This is for people in the future as I know this previous post is 2 months old and I'm sure you've come up with a solution. But for future reference:

```
 sudo add-apt-repository ppa:openjdk/ppa
apt-get update
apt-get install openjdk-7

```

However I have my concerns, as of 2/21/2012 the last time openjdk-7 was updated for Lucid was 2010-12-12, version "7~b117~pre1-0lucid1"  seems really old. Not sure myself on the best method to get the latest OpenJDK-7 on Ubuntu 10.04 Lucid.

---

