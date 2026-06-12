---
title: "Broken packages"
date: 2009-07-21
forum: General Help
---

### Post by hiding on 2009-07-21
I use ubuntu 8.04 (hardy) and I've recently been having problems with broken packages (apparently). 

Basically my update manager tells me I have three broken packages on my system. When I try to run an update I get the following error message:

E: /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb: failed in buffer_write(fd) (10, ret=-1)

When I run the Package Manager it tells me that the three broken packages are:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

When I try to fix these I get the same error message.

E: /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb: failed in buffer_write(fd) (10, ret=-1)

I'm stumped. I don't really understand any of this stuff and don't know how to proceed, so any help greatly appreciated.

Forgive me if I'm excluding important information or if my post displays some general ignorance. This is because I am generally ignorant.

---

### Post by wojox on 2009-07-21
In Synaptic:

Choose Edit > Fix broken packages from the menu
Choose Apply Marked Changes from Edit
Click Apply
Broken Packages usually have all red boxes next to them.

---

### Post by hiding on 2009-07-21
Thanks for your response. 

However, I have already tried this, as I attempted to explain in my original post. I wasn't clear enough, sorry. 

Anyhow, when I try to fix the package as you suggest I get the error message:

E: /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb: failed in buffer_write(fd) (10, ret=-1)

---

### Post by 3rdalbum on 2009-07-21
Remove the contents of the "/var/cache/apt/archives" directory (or at least, the offending packages).

Now try removing and installing Java.

If you get a text-based license agreement screen appearing when you install Java, you need to press the Tab key in order to highlight the "I agree" button, and then press the space bar to "click" it.

---

### Post by hiding on 2009-07-21
Thanks for your response 3rdalbum. 

I just tried following your advice. I removed all the sun-java deb files, as suggested, but afterwards when I tried to remove java, the add/remove programs application gave me the following error message:

Failed to check for installed and available applications. 

This is a major failure of your software management system. Please check for broken packages with synaptic

...and so on. Thoughts?

---

### Post by hiding on 2009-07-21
Does anyone have any ideas about this? It is deeply frustrating as I am currently unable to perform any updates. Also, ubuntu is behaving strangely in other ways (e.g. not opening certain types of files). I'm not sure if this is related.

---

### Post by michy99 on 2009-07-21
What happens of you run this command in a terminal?```
sudo dpkg --configure -a
```

---

### Post by hiding on 2009-07-21
sudo dpkg --configure -a

gives error message as follows:

dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-14-0ubuntu1.8.04) | ia32-sun-java6-bin (= 6-14-0ubuntu1.8.04); however:
  Version of sun-java6-bin on system is 6-07-3ubuntu2.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-14-0ubuntu1.8.04); however:
  Version of sun-java6-bin on system is 6-07-3ubuntu2.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jre
 sun-java6-plugin

---

### Post by michy99 on 2009-07-21
What about this?```
sudo apt-get --reinstall install sun-java6-bin
```

---

### Post by hiding on 2009-07-21
sudo apt-get --reinstall install sun-java6-bin

gives the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
2 not fully installed or removed.
Need to get 29.1MB of archives.
After this operation, 4633kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse sun-java6-bin 6-14-0ubuntu1.8.04 [29.1MB]
Fetched 29.1MB in 1min1s (476kB/s)                                             
Preconfiguring packages ...
(Reading database ... 132731 files and directories currently installed.)
Preparing to replace sun-java6-bin 6-07-3ubuntu2 (using .../sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/rt.jar': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.8.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by michy99 on 2009-07-21
Aha! I think we have a clue here..```
No space left on device
```What do you get for this command?```
df -h
```You may be out of space in your / partition.

---

### Post by hiding on 2009-07-21
Aha...

df -h

gives us the following

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.7G     0 100% /
varrun                220M  120K  220M   1% /var/run
varlock               220M     0  220M   0% /var/lock
udev                  220M   44K  220M   1% /dev
devshm                220M   24K  220M   1% /dev/shm
lrm                   220M   40M  181M  18% /lib/modules/2.6.24-24-generic/volatile
/dev/sda3             272G  146G  113G  57% /home
overflow              1.0M   76K  948K   8% /tmp
gvfs-fuse-daemon      3.7G  3.7G     0 100% /home/ian/.gvfs

Now even with my generally weak grip on what all this means I think I understand what the top line of this table is telling us.

Knowing what to do about it is another matter of course...

---

### Post by grayn0de on 2009-07-21
Have you tried removing the installation packages?
```
sudo apt-get autoclean
```

also, in my experience 3.7GB is a little small for a / partition, these days. You could try resizing the partitions with something like gparted live or similar. It looks like you have a bit of space left to move over from your /home partition. I would say at least 6GB total for / would be good, provided you keep up with the maintenance and cleaning. (Make a good backup before resizing, of course.)

---

### Post by michy99 on 2009-07-21
Yep, / on /dev/sda1 is only 3.7G and it is full. As a temporary solution```
sudo apt-get clean
``` might free up some space. For a more permanent solution, I suggest you use gparted to shrink another partition and add to /dev/sda1. I would suggest 10G as a minimum. That should probably be enough, since you have /home on another partition.

---

### Post by hiding on 2009-07-21
Well, I understand in general terms what's being advised, but that doesn't stop it from being massively daunting! I'll give it a try though...

Thanks for getting me this far.

---

