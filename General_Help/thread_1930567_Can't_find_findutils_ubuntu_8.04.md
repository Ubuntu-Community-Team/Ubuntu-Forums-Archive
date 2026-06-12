---
title: "Can't find findutils ubuntu 8.04"
date: 2012-02-23
forum: General Help
---

### Post by lennih on 2012-02-23
I can't find the package findutils 4.4.0-2 for Ubuntu 8.04 anywhere.

Nor can I find 
sudo wget [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.2_i386.deb)
sudo wget [http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.9-4ubuntu6.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.9-4ubuntu6.2_i386.deb)

Any help will be appreciated. Thanks!

---

### Post by oldos2er on 2012-02-23
Post moved to its own thread.

The desktop version of 8.04 is no longer supported, its repositories have been moved to old-releases. [http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

---

### Post by savanna on 2012-02-24
Hi Lennih,

You just need to switch your apt **sources.list** file to point to the old-releases repository. I've described how to do it on my blog - **[apt sources.list for old versions of Ubuntu]("http://www.snowfrog.net/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/")**

Then things like **sudo apt-get install findutils** will work.

---

