---
title: "Sypnatic Problems"
date: 2009-08-04
forum: General Help
---

### Post by dannied on 2009-08-04
I'm running Ubuntu 9.04 and I'm trying to add programs. Every time I go to the add/remove client an error comes out. It reads:

[I]Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]


Here is what I have done so far: 

tracielay@tracielay-laptop:~$ '/etc/apt/sources.list'
bash: /etc/apt/sources.list: Permission denied
tracielay@tracielay-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
tracielay@tracielay-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [62.3kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [129kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2391B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [18.1kB]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [522B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [24.0kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2391B] 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [39.4kB]       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B]     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B]    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [522B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [43.5kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [12.1kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [3933B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [1349B]
Fetched 445kB in 2s (149kB/s)                  
Reading package lists... Done
tracielay@tracielay-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.1MB of archives.
After this operation, 1692kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 153896 files and directories currently installed.)
Preparing to replace sun-java6-bin 6-13-1 (using .../sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb (--unpack):
 trying to overwrite `/usr/lib/jvm/java-6-sun', which is also in package tersus
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tracielay@tracielay-laptop:~$ 
tracielay@tracielay-laptop:~$ 




Any help? I'm new to this.

---

### Post by Moop on 2009-08-04
Open up Synaptic. System-Administration-Synaptic Package Manager. On the lower left click on custom filters, on the top left click on broken. Is anything listed? Go to Edit-Fix Broken Packages and finally click reload. 

To look at your software sources System-Administration-Software Sources.

---

