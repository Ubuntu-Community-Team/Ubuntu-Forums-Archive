---
title: "Can't install packages"
date: 2010-12-02
forum: General Help
---

### Post by Xinerama on 2010-12-02
Man oh man,
I'm glad you all are here to help people like me.
Anyway, yesterday I uninstalled IcedTea and that's when my problems started.
This is what I've done.  Downloaded the needed files and then:
```

root@elias-desktop:/home/elias/Desktop/debfiles# dpkg -i --force-all odbcinst_2.2.11-21_i386.deb 
(Reading database ... 
dpkg: warning: files list file for package `odbcinst' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 312199 files and directories currently installed.)
Preparing to replace odbcinst 2.2.11-21 (using odbcinst_2.2.11-21_i386.deb) ...
Unpacking replacement odbcinst ...

```

It just hangs, and hangs, and hangs there.  It'll never quit.

I have a bunch of packages to install and I don't know the best way to go about doing this.  Here's the list of needed packages + dependencies.

```

bind9-host_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb   liblwres60_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb
dnsutils_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb     odbcinst1debian1_2.2.11-21_i386.deb
libbind9-60_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb  odbcinst_2.2.11-21_i386.deb
libdns64_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb    
libisc60_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb     sun-java6-bin_6.22-0ubuntu1~10.04_i386.deb
libisccc60_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb   sun-java6-jre_6.22-0ubuntu1~10.04_all.deb
libisccfg60_1%3a9.7.0.dfsg.P1-1ubuntu0.1_i386.deb  unixodbc_2.2.11-21_i386.deb


```

---

### Post by lobralleo on 2010-12-02
It looks like all of the packages you need come from Ubuntu repositories, so there is no need to install them manually. You should be able to install them and all the needed dependencies directly from Synaptic.

To open Synaptic, go to System > Synaptic Package Manager and search your packages using the Search button. When you find them, right-click on them and mark them for installation: Synaptic will do the rest.

Good luck!

---

### Post by Xinerama on 2010-12-02
Thanks for the quick response.
I tried that, but it still hangs.
Here is what happened when I tried to install java.

```

root@elias-desktop:/home/elias/Desktop/debfiles# dpkg -i --force-overwrite sun-java6-bin_6.22-0ubuntu1~10.04_i386.deb 
Selecting previously deselected package sun-java6-bin.
(Reading database ... 
dpkg: warning: files list file for package `odbcinst' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 312199 files and directories currently installed.)
Unpacking sun-java6-bin (from sun-java6-bin_6.22-0ubuntu1~10.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted


```

---

### Post by lobralleo on 2010-12-02
What if you use apt-get instead?
Try and type this into the terminal:

```
sudo apt-get install sun-java6-bin sun-java6-jre
```

---

### Post by Xinerama on 2010-12-02
Okay, so here's what I've done.
Seriously I can't install those packages.  Apt-get just hangs.  Anyway, I tried the following:

```

gedit /etc/fstab
     added cdrom line
/dev/sr0	/cdrom		auto	ro,noauto,user,exec	0	0
 
mount -a
 
apt-cdrom add
apt-cdrom ident
gedit /etc/apt/sources.list
     comment out other sources *except CDROM*
apt-get update 
     to update the *newly modified* sources.list
   lastly tried
apt-get install --reinstall odbcinst
   not found
   and this one, which I KNEW would NOT be found
apt-get install --reinstall sun*

```

I'll try your suggestion again, but somehow the dpkg, (i think) database is broken.  Maybe not though.

I can't launch Synaptic anymore, because it really needs **odbcinst**

---

### Post by Xinerama on 2010-12-02
Dear lobralleo:

IT WORKED!!!!
I don't understand how or why.  Maybe when I updated the "sources.list".  I have no idea.
Here's my /etc/apt/sources.list if you're in Seoul, South Korea.

```

deb http://kr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse

 deb http://kr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

deb http://kr.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse

deb http://kr.archive.ubuntu.com/ubuntu/ lucid main universe restricted multiverse

```
I guess we can mark this as SOLVED!!  I wish I knew how.

---

### Post by lobralleo on 2010-12-02
Glad to hear that!

Before marking the thread as solved, it might be worth to investigate this issue a little more to offer a crisp solution to anybody else with the same problem: let's try and see if we can figure out what went wrong in the first place, or find some similar thread. I am going to look into apt-get and dpkg to see if I can find an interpretation for what happened to you.

Any ideas out there, everybody? :)

---

### Post by Xinerama on 2010-12-02
Okay, I don't have an answer exactly, but here are some things I noticed.
I ran ```
sudo apt-get install sun-java6-bin sun-java6-jre
``` as you had suggested and everything installed.
I know that there were some other dependencies.
Whenever I ran ```
apt-get -f install
``` it just hung.  I don't know why, but I did remove some "lock" files later from ```
rm /var/lib/dpkg/lock
and
rm /var/cache/apt/archives/lock
```So if those had anything to do with the process I'm not entirely sure.
Under System -> Admin -> Software Sources -> "Ubuntu Software" tab, I chose from the "Download From:" dropdown menu -> "Other" and then "Select Best Server".  Also in the "Other Software" tab, it went from 4 checked boxes to just one, the first one ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner).
That's pretty much it.
I think it had something to do with my server choices and order of operations for your "apt-get install" line.  

I'm an ex Fedora user myself and when I downloaded those packages I expected them to be able to install either locally (no internet [rpm]) with dpkg or satisfy dependencies (internet [yum]) with aptitude/apt-get.  I was trying to narrow where the problem might have been.  

Anyway, thanks for helping.  It's funny though, I must admit.  Everytime you offered a suggestion, I was like "pfffft!  I've tried that.  It's not going to work!" Then Voila!!!!  
So let this be a lesson to who ever reads this.  Make a checklist and check it twice.  Hahhaa ;)

---

