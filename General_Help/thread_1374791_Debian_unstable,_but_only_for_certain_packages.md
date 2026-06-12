---
title: "Debian unstable, but only for certain packages?"
date: 2010-01-07
forum: General Help
---

### Post by nunyez on 2010-01-07
According to [https://bugs.launchpad.net/ubuntu/+source/rtorrent/+bug/280494](https://bugs.launchpad.net/ubuntu/+source/rtorrent/+bug/280494) rtorrent is up to 0.8.5 in debian unstable. I'm not sure that I want to add it to my sources and sync with all unstable packages.

Both libtorrent/rtorrent are required to upgrade. Would I have to add it to my sources list, apt-get those two packages, then remove it from my sources list?  Or something else?

---

### Post by slakkie on 2010-01-07
Have a look on my blog, there is a an article about using the preferences file which could be what you need :)

---

### Post by nunyez on 2010-01-20
Hello, here's what I've got so far.  I'm running karmic and i've added lucid because I want a newer versions of rtorrent/libtorrent without compiling myself (as the ones I currently run are 0.8.4/0.12.4). The latest versions are 0.8.6/0.12.6 but I need 0.8.5/0.12.5 for now.

Here's what I don't understand:
```
noon@hotkarl:~$ apt-cache policy rtorrent 
rtorrent:
  Installed: 0.8.4-1
  Candidate: 0.8.5-2
  Package pin: 0.8.5-2
  Version table:
     0.8.5-2 990
        -10 http://us.archive.ubuntu.com lucid/universe Packages
 *** 0.8.4-1 990
        100 /var/lib/dpkg/status
     0.8.2-0ubuntu2 990
        990 http://us.archive.ubuntu.com karmic/universe Packages
noon@hotkarl:~$ apt-cache policy libtorrent11
libtorrent11:
  Installed: 0.12.2-0ubuntu2
  Candidate: 0.12.5-2
  Package pin: 0.12.5-2
  Version table:
     0.12.5-2 990
        -10 http://us.archive.ubuntu.com lucid/universe Packages
 *** 0.12.2-0ubuntu2 990
        990 http://us.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status

```
... and then ...
```
noon@hotkarl:~$ sudo apt-get upgrade
[sudo] password for noon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libtorrent11 rtorrent
The following packages will be upgraded:
..blahblahblah
```

Why are they being held back? It lists both newer versions as candidates under lucid and my pin version is equal to what I want them to be.
--------------------------------------------------------
Here are all of my preferences/modifications:

I've made /etc/apt/apt.conf.d/01ubuntu like so, even though i think its useless:
```
APT::Default-Release "karmic";
```

Here's my /etc/apt/preferences:
```
# Do not allow lucid
Package: *
Pin: release a=lucid
Pin-Priority: -10

Package: *
Pin: release a=lucid-updates
Pin-Priority: -10

Package: *
Pin: release a=lucid-security
Pin-Priority: -10

Package: *
Pin: release a=lucid-proposed
Pin-Priority: -10

# Now allow karmic updates
Package: *
Pin: release a=karmic
Pin-Priority: 990

Package: *
Pin: release a=karmic-updates
Pin-Priority: 990

Package: *
Pin: release a=karmic-security
Pin-Priority: 990

Package: *
Pin: release a=karmic-backports
Pin-Priority: 990

Package: *
Pin: release a=karmic-proposed
Pin-Priority: 990

# newer lucid rtorrent/libtorrent 0.12.5/0.8.5
Package: libtorrent11
Pin: version 0.12.5*
Pin-Priority: 990

Package: rtorrent
Pin: version 0.8.5*
Pin-Priority: 990

```

Here's my additions to /etc/apt/sources.list (otherwise a standard karmic):
```
# Add lucid debs for testing versions
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
```

---

### Post by nunyez on 2010-01-21
Well I guess that they are probably being held back because of rtorrent's dependencies: [http://packages.ubuntu.com/lucid/rtorrent](http://packages.ubuntu.com/lucid/rtorrent)

How do you approach packages such as this one with this many dependencies? Add an entry for each on /etc/apt/preferences ?

Edit: Well adding each to /etc/apt/preferences doesnt seem to have helped:

```
noon@hotkarl:/etc/apt$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  libc6 libcurl3 libgcc1 libssl0.9.8 libstdc++6 libtorrent11 rtorrent

```

Same as previous post but with the dependencies added:
```

# newer rtorrent/libtorrent 0.12.5/0.8.5
# rt dependencies..
Package: libc6
Pin: release a=lucid
Pin-Priority: 990

Package: libcurl3
Pin: release a=lucid
Pin-Priority: 990

Package: libgcc1
Pin: release a=lucid
Pin-Priority: 990

Package: libncursesw5
Pin: release a=lucid
Pin-Priority: 990

Package: libsigc++2.0-0c2a
Pin: release a=lucid
Pin-Priority: 990

Package: libssl0.9.8
Pin: release a=lucid
Pin-Priority: 990

Package: libstdc++6
Pin: release a=lucid
Pin-Priority: 990

Package: libxmlrpc-c3
Pin: release a=lucid
Pin-Priority: 990

Package: libxmlrpc-core-c3
Pin: release a=lucid
Pin-Priority: 990

Package: libtorrent11
Pin: version 0.12.5*
Pin-Priority: 990

Package: rtorrent
Pin: version 0.8.5*
Pin-Priority: 990

```

---

### Post by slakkie on 2010-01-21
If you set lucid to a pin prio of 100 it will install the dependencies if it cannot satisfy them with Karmic's version. ATM you don't allow them to be installed (-10 prio).

Lemme know if this is the case. Please use aptitude -s in order to simulate the action it would normally perform.

```

Package: *
Pin: release a=lucid
Pin-priority: 100

# Same for -updates, -proposed, etc etc.
Package: *
Pin: release a=karmic
Pin-priority: 990

Package: hello
Pin: version 1.1*
Pin-priority: 990

```

If hello 1.1.8 is in Lucid and it has dependencies in lucid, those will be satisfied. With the -10 you gave Lucid, apt is unable to satisfy the dependencies and holds the packages back.

---

