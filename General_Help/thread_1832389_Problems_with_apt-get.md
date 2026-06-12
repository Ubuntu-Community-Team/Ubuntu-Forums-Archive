---
title: "Problems with apt-get"
date: 2011-08-24
forum: General Help
---

### Post by dachinster on 2011-08-24
Hi guys,

I am running Ubuntu 11.04 and getting some problems with running apt-get update and install.

When I run sudo apt-get update, I get this output at the end of the listing:

> Fetched 409 kB in 5s (72.7 kB/s)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release)  rename failed, Input/output error (/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_Release -> /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_Release).

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources  rename failed, Input/output error (/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources.decomp -> /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources).

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources  rename failed, Input/output error (/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources.decomp -> /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources).

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages  rename failed, Input/output error (/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages.decomp -> /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages).

E: Some index files failed to download. They have been ignored, or old ones used instead.
When I try to run sudo apt-get upgrade I get the following message:

> ubuntu@ubuntu:~$ sudo apt-get upgrade -y
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages
E: Problem renaming the file /var/cache/apt/pkgcache.bin.cOMIly to /var/cache/apt/pkgcache.bin - rename (5: Input/output error)
E: The package lists or status file could not be parsed or opened.Also, when I try to run dpkg I get this:
> ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: reading package info file '/var/lib/dpkg/status': Input/output error
Some of you may ask for my sources, so I am adding it in here:

> ubuntu@ubuntu:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
Upon launch, the GUI Synaptic Package Manager gives the following error message before crashing completely:

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages
E: Problem renaming the file /var/cache/apt/pkgcache.bin.LgBkm5 to /var/cache/apt/pkgcache.bin - rename (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.



Could any of you assist with all these issues?

---

### Post by jerrrys on 2011-08-25
i think post #3 is what your looking for

[http://ubuntuforums.org/showthread.php?t=1806416](http://ubuntuforums.org/showthread.php?t=1806416)

---

### Post by dachinster on 2011-08-25
Hi jerrrys

Thanks for the assistance but that didn't work. After the update, I still got the exact same problem as before.

---

### Post by grubu on 2011-08-25
Hello dachinster,

you could try a deletion of those two files:
```

/var/cache/apt/pkgcache.bin
/var/cache/apt/srcpkgcache.bin

```and then run again sudo apt-get update

You might also find some helpful lines here although it is german:
[http://wiki.ubuntuusers.de/apt-get](http://wiki.ubuntuusers.de/apt-get)

---

### Post by jerrrys on 2011-08-25
sudo rm /var/cache/apt/*.bin

---

### Post by grubu on 2011-08-25
Dachinster, if this all might not help have a look into thread [B][SOLVED] sudo apt-get install   error
[/B]at here: [http://ubuntuforums.org/showthread.php?t=727892](http://ubuntuforums.org/showthread.php?t=727892)

---

