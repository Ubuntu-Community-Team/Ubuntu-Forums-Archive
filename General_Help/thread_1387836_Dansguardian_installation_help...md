---
title: "Dansguardian installation help.."
date: 2010-01-22
forum: General Help
---

### Post by karthick87 on 2010-01-22
I cant able to install dansguardian i get the following error..

karthick@Learners-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Reading package lists... Done
karthick@Learners-desktop:~$ sudo apt-get install dansguardian tinyproxy fireholReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aggregate
The following NEW packages will be installed:
  aggregate dansguardian firehol tinyproxy
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 727kB of archives.
After this operation, 3609kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe aggregate 1.6-4
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe dansguardian 2.9.9.7-2ubuntu1
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe firehol 1.256-4
  403 Forbidden
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe tinyproxy 1.6.3-3.2
  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/a/aggregate/aggregate_1.6-4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/aggregate/aggregate_1.6-4_i386.deb)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/dansguardian/dansguardian_2.9.9.7-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/dansguardian/dansguardian_2.9.9.7-2ubuntu1_i386.deb)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/f/firehol/firehol_1.256-4_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/f/firehol/firehol_1.256-4_all.deb)  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/tinyproxy/tinyproxy_1.6.3-3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/tinyproxy/tinyproxy_1.6.3-3.2_i386.deb)  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
karthick@Learners-desktop:~$ 


How to solve this issue???

---

### Post by Saiko Berry on 2010-01-22
sudo apt-get install dansguardian tinyproxy fireholReading --fix-missing?

---

### Post by karthick87 on 2010-02-02
Bump..

---

