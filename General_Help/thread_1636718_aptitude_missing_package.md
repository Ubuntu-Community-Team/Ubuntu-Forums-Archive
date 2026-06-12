---
title: "aptitude missing package"
date: 2010-12-03
forum: General Help
---

### Post by furf on 2010-12-03
<!-- Warning: ubuntu newb

I'm trying to get an Ubuntu 10.10 server up and running. I need to install some compilers, so I used: aptitude install build-essential -y

Unfortunately, there seem to be one or more missing packages, specifically linux-libc-dev

The install bombs when it can't find: linux-libc-dev_2.6.35-1022.34_amd64.deb

I looked in the package directory: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/](http://security.ubuntu.com/ubuntu/pool/main/l/linux/)

I couldn't find: linux-libc-dev_2.6.35-1022.34_amd64.deb

But I did find: linux-libc-dev_2.6.35-1022.33_amd64.deb

What is the best way to resolve this? Manual install? Add more repos to the sources.list?

Install dump and sources.list below...

Thanks in advance.

# sudo aptitude install build-essential -y

The following NEW packages will be installed:
  build-essential dpkg-dev{a} fakeroot{a} g++{a} g++-4.4{a} gcc{a} gcc-4.4{a} 
  libalgorithm-diff-perl{a} libalgorithm-merge-perl{a} libc-dev-bin{a} libc6-dev{a} 
  libdpkg-perl{a} libgomp1{a} libstdc++6-4.4-dev{a} linux-libc-dev{a} 
  manpages-dev{a} 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.9MB of archives. After unpacking 51.6MB will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libc-dev-bin amd64 2.12.1-0ubuntu6 [226kB]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main linux-libc-dev amd64 2.6.35-1022.34
  404  Not Found [IP: 91.189.88.40 80]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libc6-dev amd64 2.12.1-0ubuntu6 [2738kB]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-libc-dev amd64 2.6.35-1022.34
  404  Not Found [IP: 91.189.88.37 80]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libgomp1 amd64 4.5.1-7ubuntu2 [25.4kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main gcc-4.4 amd64 4.4.4-14ubuntu5 [2961kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main gcc amd64 4:4.4.4-1ubuntu2 [5070B]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libstdc++6-4.4-dev amd64 4.4.4-14ubuntu5 [1563kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main g++-4.4 amd64 4.4.4-14ubuntu5 [5605kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main g++ amd64 4:4.4.4-1ubuntu2 [1448B]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libdpkg-perl all 1.15.8.4ubuntu3 [504kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main dpkg-dev all 1.15.8.4ubuntu3 [772kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main build-essential amd64 11.5 [7228B]
Get:12 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main fakeroot amd64 1.14.4-1ubuntu1 [101kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libalgorithm-diff-perl all 1.19.02-1 [51.3kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libalgorithm-merge-perl all 0.08-1 [13.0kB]
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main manpages-dev all 3.24-1ubuntu1 [1567kB]
Fetched 16.1MB in 4s (3495kB/s)  
Selecting previously deselected package libdpkg-perl.
(Reading database ... 15719 files and directories currently installed.)
Unpacking libdpkg-perl (from .../libdpkg-perl_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libgomp1.
Unpacking libgomp1 (from .../libgomp1_4.5.1-7ubuntu2_amd64.deb) ...
Selecting previously deselected package gcc-4.4.
Unpacking gcc-4.4 (from .../gcc-4.4_4.4.4-14ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.4.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-1_all.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-1_all.deb) ...
Selecting previously deselected package libc-dev-bin.
Unpacking libc-dev-bin (from .../libc-dev-bin_2.12.1-0ubuntu6_amd64.deb) ...
Selecting previously deselected package manpages-dev.
Unpacking manpages-dev (from .../manpages-dev_3.24-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up libdpkg-perl (1.15.8.4ubuntu3) ...
Setting up dpkg-dev (1.15.8.4ubuntu3) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libgomp1 (4.5.1-7ubuntu2) ...
Setting up gcc-4.4 (4.4.4-14ubuntu5) ...
Setting up gcc (4:4.4.4-1ubuntu2) ...
Setting up libalgorithm-diff-perl (1.19.02-1) ...
Setting up libalgorithm-merge-perl (0.08-1) ...
Setting up libc-dev-bin (2.12.1-0ubuntu6) ...
Setting up manpages-dev (3.24-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1022.34_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1022.34_amd64.deb:) 404  Not Found [IP: 91.189.88.37 80]

# vi sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe

---

### Post by snowpine on 2010-12-03
Try prefacing the command with "sudo aptitude update" and let me know if that solves the problem. :)

---

