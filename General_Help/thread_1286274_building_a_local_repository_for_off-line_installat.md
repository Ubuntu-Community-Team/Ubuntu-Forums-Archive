---
title: "building a local repository for off-line installation"
date: 2009-10-08
forum: General Help
---

### Post by linuxUser1 on 2009-10-08
I need to build a local repository for off-line installation. The machine being used to build the repository is running Ubuntu 9.04 for amd64. The packages I need to download and their dependencies are for Ubuntu 9.04 for i386. Here is an example of what I have so far.

```
[INDENT]export PACKAGES="build-essential wireless-tools"[/INDENT][INDENT]export MYREPO=/path/to/my/repo
[/INDENT][INDENT]export MYSOURCES=/path/to/my/sources.list
[/INDENT][INDENT]sudo apt-get build-dep --download-only --reinstall --no-install-recommends --yes -o APT::Architecture=i386 -o Dir::Etc::SourceList=$MYSOURCES -o Dir::Cache::Archives=$MYREPO $PACKAGES

sudo apt-get install --download-only --reinstall --no-install-recommends --yes -o APT::Architecture=i386 -o Dir::Etc::SourceList=$MYSOURCES -o Dir::Cache::Archives=$MYREPO $PACKAGES
[/INDENT]
```It works until I add the Architecture argument. Once I add the Architecture argument then it cannot find any of the packages. The error looks like this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
```My sources list looks like this...[INDENT]```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
```[/INDENT]I have found multiple old forum discussions of people trying to do this with really ugly solutions like scripts that manually resolve dependencies 3 levels deep etc. Also, I have looked at aptoncd but I really don't think it is necessary to accomplish this and I don't know if it will let me grab stuff for another system since it is really a backup tool. To avoid some of the obvious answers... I know I could do this with a chroot, or a virtual machine, or multiboot but that is not what I am asking. 

Thanks in advance!

---

