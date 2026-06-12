---
title: "I can't install java on Ubuntu 10.04??"
date: 2010-11-19
forum: General Help
---

### Post by VyperX on 2010-11-19
OK, so when I try to install java through the software center, I keep getting an error that says:

> Failed to fetch http: //us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010j-0ubuntu0.10.04_all.deb 404  Not Found [IP: 91.189.88.30 80]

I also have already tried to install a .bin file which I got from java.com and it still doesn't work. please help me!

Thank you

P.S: I am using Ubuntu 10.04

---

### Post by cgroza on 2010-11-19
What is the output of : sudo apt-get update?

---

### Post by VyperX on 2010-11-19
> **cgroza said:**
> What is the output of : sudo apt-get update?

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US              
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:6 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,082B]                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Get:10 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [11.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [98.5kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [345kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [35.1kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [47.5kB]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [12.9kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [2,003B]  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [660B]     
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [135kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [149kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [57.3kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [7,366B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [3,677B]
Fetched 1,006kB in 3s (306kB/s)                             
Reading package lists... Done

---

### Post by cgroza on 2010-11-20
The repos seem fine.

---

### Post by HannuMR on 2010-11-20
First you must have "ubuntu lucid partner" in updates.
Hope you understand in picture even my language:

[http://www.freeimagehosting.net/uploads/0d6cdb216c.png](http://www.freeimagehosting.net/uploads/0d6cdb216c.png)

Then install three packages for Sun Java in Synaptic:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

And remove openJDK

Or if you want to use OpenJava, it and ewerything else comes in Terminal:

[FONT=Arial][SIZE=2]sudo apt-get install ubuntu-restricted-extras[/SIZE][/FONT]

---

