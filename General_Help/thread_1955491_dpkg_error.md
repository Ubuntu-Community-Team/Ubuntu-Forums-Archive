---
title: "dpkg error"
date: 2012-04-09
forum: General Help
---

### Post by Vuxee on 2012-04-09
I'm trying to install some build dependencies and I get this error I've not come across before.

```
root@bulb:~# apt-get install build-essential libssl-dev libperl-dev pkg-config libc-ares-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cpp cpp-4.5 dpkg-dev fakeroot g++ g++-4.5 gcc gcc-4.5 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libc-ares2 libc-dev-bin
  libc6-dev libcloog-ppl0 libdpkg-perl libelfg0 libgmp3c2 libgmpxx4ldbl libmpc2 libmpfr4 libppl-c2 libppl7 libstdc++6-4.5-dev libtimedate-perl
  linux-libc-dev manpages-dev patch zlib1g-dev
Suggested packages:
  cpp-doc gcc-4.5-locales debian-keyring g++-multilib g++-4.5-multilib gcc-4.5-doc libstdc++6-4.5-dbg gcc-multilib autoconf automake1.9 libtool flex bison
  gdb gcc-doc gcc-4.5-multilib libmudflap0-4.5-dev libgcc1-dbg libgomp1-dbg libmudflap0-dbg binutils-gold glibc-doc libstdc++6-4.5-doc diffutils-doc
The following NEW packages will be installed:
  build-essential cpp cpp-4.5 dpkg-dev fakeroot g++ g++-4.5 gcc gcc-4.5 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libc-ares-dev libc-ares2 libc-dev-bin libc6-dev libcloog-ppl0 libdpkg-perl libelfg0 libgmp3c2 libgmpxx4ldbl libmpc2 libmpfr4 libperl-dev libppl-c2
  libppl7 libssl-dev libstdc++6-4.5-dev libtimedate-perl linux-libc-dev manpages-dev patch pkg-config zlib1g-dev
0 upgraded, 34 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/33.6 MB of archives.
After this operation, 101 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable.
dpkg: error: 2 expected programs not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@bulb:~#

```Does this mean anything?

---

### Post by AlexOnVinyl on 2012-04-09
Try this:

```
sudo find / -name ldconfig
```

then post the output of that

then try the same for the other processes

```
sudo find / -name start-stop-daemon
```

this will find where these are is located. 

From what it sounds like - and anyone is all welcome to correct me if I'm wrong, but it sounds like your dpkg path is pointing to a locations that no longer houses the packages.

but I may be wrong.

If none of those work you could always try

```
sudo apt-get -f install
```

and see if it installs anyways.

---

### Post by r-senior on 2012-04-09
What command did you use to get the root prompt?

Did you try the same command with sudo?

---

