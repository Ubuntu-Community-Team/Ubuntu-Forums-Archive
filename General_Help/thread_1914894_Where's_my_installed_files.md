---
title: "Where's my installed files"
date: 2012-01-25
forum: General Help
---

### Post by sincos2007 on 2012-01-25
Hi all,

I want to know where is my installed files after each time I install a software. And Is it possible to specify the install path. If the software is open source software, where's those source files.

Thanks.

---

### Post by sanderd17 on 2012-01-25
Most software you install is binary packages (as it's faster to install, and it's smaller to download). To get the source, there are source packages available, but it's possible that you will have to activate the source repositories.

As to where your files are installed, when you unpack a .deb file, you see it contains a few installation scripts, but you'll also see that there is a part of the filesystem in that deb. So the deb is just extracted to the right places in the filesystem.

The task of a distribution is to make sure that those installation locations don't collide. I don't see why you would want to change the installation location.

---

### Post by drmrgd on 2012-01-25
You can also check the details of an installed package using dpkg (assuming you used the package manager to install and didn't manually compile).  Check out the -S or -L switches as they'll tell you what files are associated with the package and where they're located.  You might run ```
dpkg --help
``` to find out the availble options for the package manager to see what will work for you.

---

### Post by jerrrys on 2012-01-25
For all file locations you can use synaptic package manager.  It will list all files installed and all dependencies.

[ATTACH]211410[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

To install; copy and paste in terminal:  sudo apt-get install synaptic

---

### Post by sincos2007 on 2012-01-26
Great tool. I will try it.

---

### Post by oldos2er on 2012-01-26
```
dpkg -L <package name>
``` will also show where all files in a package are installed.

For source code, make sure you have any deb-src repositories enabled in /etc/apt/sources.list, then run ```
apt-get source <package name>
```

---

### Post by jerrrys on 2012-01-27
You may also want to open up your other sources.

[ATTACH]211533[/ATTACH]

---

