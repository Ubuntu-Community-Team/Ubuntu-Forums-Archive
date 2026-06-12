---
title: "list of packages for installing"
date: 2009-12-05
forum: General Help
---

### Post by prudra on 2009-12-05
I hope this is the right forum.

I am posting this thread, because some others may face the same difficulty that
I faced and may want a solution.

In my new netbook with pre-installed ubuntu-8.04.1 I could not install
gnuplot, xfig, xpdf, cabextract & wine by apt-get, bacause apt-get could not find them.
Synaptic also failed. I have cn.archive.ubuntu.co, us.archive.ubuntu.com &
archive.canonical.com in /etc/apt/sources.list

On a hunch (because Ubuntu & Debian are so connected) I downloaded these files
from Debian package list and installed by sudo dpkg -i  xxxx.deb
There were, of course, some, but not many, dependency problems  and some new
packages had also to be installed.

I request you to store these packages also in the archives

---

### Post by othiena on 2009-12-05
they are in the repositories.

make sure you have all possible repositories enabled.

---

### Post by endBc on 2009-12-05
Better show us your /etc/apt/sources.list.

---

### Post by prudra on 2009-12-05
> **endBc said:**
> Better show us your /etc/apt/sources.list.
I am attaching it as sources.list.txt
Thanks.
P.Rudra.

---

### Post by ankspo71 on 2009-12-05
Hi,

Have you tried clicking on the reload button in synaptic package manager? 
You can also use this code in the terminal since I see you are familiar with apt-get commands:

```
sudo apt-get update && sudo apt-get upgrade
```

That will update your repository cache and download any updates (if any), and will hopefully allow you to install the packages you need too.

Hope this helps.
James

---

### Post by prudra on 2009-12-06
> **ankspo71 said:**
> Hi,

Have you tried clicking on the reload button in synaptic package manager? 
You can also use this code in the terminal since I see you are familiar with apt-get commands:

```
sudo apt-get update && sudo apt-get upgrade
```That will update your repository cache and download any updates (if any), and will hopefully allow you to install the packages you need too.

Hope this helps.
James

Yes, I had run them. Every time at the end of the run I got the message:

W: Failed to fetch
     [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)
     [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release)
     [http://cn.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://cn.archive.ubuntu.com/ubuntu/dists/hardy/Release)

Unable to find expected entry  contrib/binary-i386/Packages  in Meta-index file
(malformed Release file?)
E: Some index files failed to download, they have been ignored, or old ones used
    instead.

---

