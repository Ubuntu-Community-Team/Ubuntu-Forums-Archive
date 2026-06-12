---
title: "dpkg broken? Ubuntu broken?.."
date: 2006-04-04
forum: General Help
---

### Post by thefaint on 2006-04-04
Hello,

when I try to install some package it tells me to do "apt-get -f install".. so I did it and look what's happens: 

```
root@Melior:/root/dpkg# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  binutils coreutils cpio dpkg gcc-4.0-base libacl1 libattr1 libc6 libdb4.2 libgcc1 libgdbm3 libncurses5 libstdc++6 make patch perl perl-base perl-modules
Suggested packages:
  binutils-doc apt locales glibc-doc ed libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  libgpmg1 perl-doc
The following NEW packages will be installed:
  binutils coreutils cpio dpkg gcc-4.0-base libacl1 libattr1 libc6 libdb4.2 libgcc1 libgdbm3 libncurses5 libstdc++6 make patch perl perl-base perl-modules
0 upgraded, 18 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 4872kB/17.5MB of archives.
After unpacking 66.4MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://en.archive.ubuntu.com breezy-updates/main libc6 2.3.5-1ubuntu12.5.10.1 [4872kB]
Fetched 4872kB in 5m51s (13.9kB/s)
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptorE: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor
Preconfiguring packages ...
dpkg: error processing /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb (--unpack):
 subprocess dpkg-split killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

HELP ? ](*,)

---

### Post by NewbieNik on 2006-04-04
can you run apt-get upgrade or apt-get update?

---

### Post by thefaint on 2006-04-04
it's the same story..
```
root@Melior:/root/dpkg# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  dpkg-dev: Depends: dpkg (>= 1.13.1) but it is not installed
            Depends: perl5
            Depends: perl-modules but it is not installed
            Depends: cpio (>= 2.4.2-2) but it is not installed
            Depends: patch (>= 2.2-1) but it is not installed
            Depends: make but it is not installed
            Depends: binutils but it is not installed
  dselect: Depends: libc6 (>= 2.3.4-1) but it is not installed
           Depends: libgcc1 (>= 1:4.0.1) but it is not installed
           Depends: libncurses5 (>= 5.4-5) but it is not installed
           Depends: libstdc++6 (>= 4.0.1) but it is not installed
           Depends: dpkg (>= 1.13.1) but it is not installed
  libdb1-compat: Depends: libc6 (>= 2.3.2.ds1-4) but it is not installed
  rinetd: Depends: libc6 (>= 2.1.2) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by NewbieNik on 2006-04-04
Pants! Sorry, at the moment thats beyond my knowledge and capability, but I will let you know if I find anything out.
Drastic measure, if you haven't got any data to lose, could be a re-install.

although....Try listing the broken packages in the package manager and removing them, then re-installing. Not near a linux base at the moment so can't be much clearer until later.

---

### Post by thefaint on 2006-04-04
re-install is bad thing.. this is my mini-router for my little network of 100 users(in my block)

---

### Post by vruum on 2006-04-04
it complains about debconf being missing. could you try to see if debconf is properly installed. Either from synaptic or with dpkg -s debconf . ?

---

### Post by thefaint on 2006-04-04
```
root@Melior:/root/dpkg# dpkg -s debconf
Segmentation fault

```
... ?

---

### Post by vruum on 2006-04-04
okay then, what does synaptic say? Also, how and when did this start?

---

### Post by thefaint on 2006-04-04
I don't have synaptic on this installed machine. 

I don't know when it happen, but when I try to apt-get install mysql-server it tells me that I need "libc6".. so I did "apt-get install libc6" and the result is this :-k

---

### Post by vruum on 2006-04-04
oddness, how did you install ubuntu? libc6 is, as far as I can tell in the base ubuntu install. Actually, most of the packages it wants to install, should already be installed.  Do you know if apt-get used to work? If you have a sudo enabled user, and does it make a difference, if you use sudo instead of the root account.

---

### Post by thefaint on 2006-04-04
The installation is only server (base) system. libc6 and more recommended packages like gcc... are not installed by default with the base system... I have tried "sudo apt-get install -f" but the results are the same..

---

### Post by vruum on 2006-04-04
well, if nothing else, the fact that apt-get suggests you install apt, and wants to pull in dpkg and coreutils as dependencies,  sounds to me like   some database somewhere is messed up. I'm not really sure how to fix it, if you can afford it in time and data, a reinstall might be the best option.

---

### Post by alphanerd on 2006-09-15
heres how I fixed the same problem

I edited /var/lib/dpkg/status 

so it only had

Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: base
Version: 1.13.10

saved the file and then did a apt-get install --reinstall dpkg

then I did 
apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

It reinstalled everything but I am on a fast connection so it took about 10 minutes.  Beats a reinstall though

---

