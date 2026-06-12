---
title: "kernel-source-2.6.12"
date: 2006-04-30
forum: General Help
---

### Post by PaulL on 2006-04-30
I've run into a compilation problem which should be trivial but isn't. 
The details: A console only server using Breezy Badger using kernel 2.6.12-9-386 (from the Ubuntu istallation disks). The source requires the kernel headers. If I run apt-get install kernel-source I am offered a list of kernels of which the latest version is 2.6.11-7. When I run apt-get update it mostly runs except for a grumble at the end about a malformed meta-index file. Obviously I've been using apt-get and I've never had a problem with other packages. 
I checked using my desktop and the synaptic package manager and it can't find 2.6.12 either.
Odd - why doesn't everybody have the same problem?
Could I use a Debian source? If so is there a package to open the deb files?
I really would appreciate somebody else trying this and letting me know what they get.

---

### Post by geek.de.nz on 2006-04-30
Have a look here:
[http://ubuntuforums.org/showthread.php?t=75443&page=5&highlight=suspend2#1](http://ubuntuforums.org/showthread.php?t=75443&page=5&highlight=suspend2#1)


At the above link you can even get hibernate to work in Linux. Just did that recently and it works like a charm ;-).

---

### Post by PaulL on 2006-04-30
I can't see the relevance - was this posted on the wrong thread?

---

### Post by geek.de.nz on 2006-04-30
OK, I mean the lines that read:[LIST=1]
[*]Install the kernel source and the tools to build it
```

apt-get -y install build-essential bin86 libncurses-dev alien
apt-get -y install linux-tree-2.6.12
[LEFT] cd /usr/src
[/LEFT]

```[LEFT]
[/LEFT]
[*]Unpack the lot
 ```

tar -xjf linux-source-2.6.12.tar.bz2
ln -s linux-source-2.6.12 linux
[LEFT] cd /usr/src/linux
[/LEFT]

```[LEFT]
[/LEFT]
[*]Install gcc-3.4 required by kernel
```

apt-get -y install gcc-3.4
CC=gcc-3.4
[LEFT] export CC[/LEFT]

```[/LIST]...

Hope that makes it more clear. You might not need the package alien to compile your kernel. Alien just installs RPMs on your system.

There is also another thread that might be more suitable, because you can make your own packages:
[http://ubuntuforums.org/showthread.php?t=56835&highlight=howto+kernel+newbies]("http://ubuntuforums.org/showthread.php?t=56835&highlight=howto+kernel+newbies")

In the other thread, you might have to go to the first page to see the original howto. Sorry, this might be different because I got different settings, i.e. my last page shows the first post.

---

### Post by PaulL on 2006-05-01
The delay was me trying that. Yes, linux-tree does grab linux-sources-2.6.12, but when I come to compile my program it complains that the .configure is not present. What I need are the sources from the Ubuntu kernel build with the .configure (which would also make building a new kernel much easier - because I could add/remove one item at a time.
I did try building a kernel (which of course left a .configure in the sources), but I couldn't get the new kernel to boot.

---

### Post by geek.de.nz on 2006-05-02
Do you mean .config? So, you want to load the old config file, so you don't have to select so many options newly from 'make menuconfig'?

If yes, have a look in you /boot directory:
```
ls -l /boot/config*
```

You probably want to copy the appropriate file from the Ubuntu distro (should be /boot/config-2.6.12-9-386 or /boot/config-2.6.12-10-386). So, do the following:
```

sudo -l
#enter password
ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cp /boot/config-2.6.12-10-386 /usr/src/linux/.config
cd /usr/src/linux
make oldconfig
make menuconfig
...

```

Hope that helps.

---

