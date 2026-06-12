---
title: "Unable to install any packages"
date: 2010-02-02
forum: General Help
---

### Post by karthick87 on 2010-02-02
I am unable to install any packages..When i go through synaptic manager and install the package it gives the following error..How to fix it?

---

### Post by darshana on 2010-02-02
Do you use any proxy server? can you explain about your network connection?

---

### Post by karthick87 on 2010-02-02
Yes i am using squid proxy server.But eventhough i disable the proxy server i get the same error.

---

### Post by karthick87 on 2010-02-06
Bump....

---

### Post by Enigmapond on 2010-02-06
Have tried other sources? Do you get the same when doing it in the terminal? What happens when you..

```
sudo apt-get update
```

---

### Post by karthick87 on 2010-02-06
karthick@Learners-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release.gpg
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Translation-en_IN
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Translation-en_IN
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe Translation-en_IN
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/multiverse Translation-en_IN
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty Release
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/main Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/restricted Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe Sources
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/multiverse Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/multiverse Sources
Reading package lists... Done

---

### Post by Enigmapond on 2010-02-06
I don't know what you're trying to install with synaptic and I don't really have a fix for that but seems you are getting through to the repos...so if you want to install a package...

```
sudo apt-get install *name of package*
```

---

### Post by karthick87 on 2010-02-06
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
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe aggregate 1.6-4
  403 Forbidden
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe dansguardian 2.9.9.7-2ubuntu1
  403 Forbidden
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe firehol 1.256-4
  403 Forbidden
Err [http://archive.ubuntu.com]("http://archive.ubuntu.com/") jaunty/universe tinyproxy 1.6.3-3.2
  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...1.6-4_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/a/aggregate/aggregate_1.6-4_i386.deb")  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...untu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/d/dansguardian/dansguardian_2.9.9.7-2ubuntu1_i386.deb")  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo....256-4_all.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/f/firehol/firehol_1.256-4_all.deb")  403 Forbidden
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...3-3.2_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/t/tinyproxy/tinyproxy_1.6.3-3.2_i386.deb")  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Enigmapond on 2010-02-06
Odd...have you tried another mirror? I don't know where you are but go to Systems->Administration->Software Sources and pick a different location rather than the main server. You can also have it check for the fastest connection if you choose other.

---

### Post by karthick87 on 2010-02-06
I choosed another location and updated apt list and now the problem was fixed..

---

### Post by Enigmapond on 2010-02-06
Glad I could help. Please mark your thread "solved".

Cheers!

---

