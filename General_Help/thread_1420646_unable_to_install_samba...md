---
title: "unable to install samba.."
date: 2010-03-03
forum: General Help
---

### Post by karthick87 on 2010-03-03
While installing samba i get the following error..How to fix it??

```

karthick@Learners-desktop:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools keyutils
The following NEW packages will be installed:
  samba smbfs
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 6048kB of archives.
After this operation, 17.4MB of additional disk space will be used.
Err http://archive.linux.duke.edu jaunty/main samba 2:3.3.2-1ubuntu3
  403 Forbidden
Err http://archive.linux.duke.edu jaunty/main smbfs 2:3.3.2-1ubuntu3
  403 Forbidden
Failed to fetch http://archive.linux.duke.edu/ubuntu/pool/main/s/samba/samba_3.3.2-1ubuntu3_i386.deb  403 Forbidden
Failed to fetch http://archive.linux.duke.edu/ubuntu/pool/main/s/samba/smbfs_3.3.2-1ubuntu3_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by karthick87 on 2010-03-05
Still not able to install the package..

```
karthick@Learners-desktop:~$ sudo apt-get update
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Hit http://archive.canonical.com jaunty Release
Hit http://ppa.launchpad.net jaunty Release.gpg                     
Ign http://ppa.launchpad.net jaunty/main Translation-en_US          
Ign http://archive.canonical.com jaunty/partner Packages                       
Ign http://archive.canonical.com jaunty/partner Sources
Hit http://archive.linux.duke.edu jaunty Release.gpg
Ign http://archive.linux.duke.edu jaunty/main Translation-en_US
Ign http://archive.linux.duke.edu jaunty/restricted Translation-en_US
Ign http://archive.linux.duke.edu jaunty/universe Translation-en_US
Ign http://archive.linux.duke.edu jaunty/multiverse Translation-en_US
Get:1 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_US           
Hit http://archive.canonical.com jaunty/partner Packages             
Hit http://ppa.launchpad.net jaunty Release                          
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://archive.linux.duke.edu jaunty Release                               
Ign http://archive.linux.duke.edu jaunty/main Sources
Ign http://archive.linux.duke.edu jaunty/restricted Sources
Ign http://archive.linux.duke.edu jaunty/main Packages
Ign http://archive.linux.duke.edu jaunty/restricted Packages
Ign http://archive.linux.duke.edu jaunty/multiverse Sources
Ign http://archive.linux.duke.edu jaunty/universe Sources
Ign http://archive.linux.duke.edu jaunty/universe Packages
Ign http://archive.linux.duke.edu jaunty/multiverse Packages
Get:2 http://ppa.launchpad.net jaunty Release [74.7kB]
Hit http://archive.linux.duke.edu jaunty/main Sources
Hit http://archive.linux.duke.edu jaunty/restricted Sources
Hit http://archive.linux.duke.edu jaunty/main Packages
Hit http://archive.linux.duke.edu jaunty/restricted Packages
Ign http://ppa.launchpad.net jaunty/main Packages                     
Ign http://ppa.launchpad.net jaunty/main Sources                      
Ign http://ppa.launchpad.net jaunty/main Packages                     
Ign http://ppa.launchpad.net jaunty/main Sources
Hit http://archive.linux.duke.edu jaunty/multiverse Sources
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://archive.linux.duke.edu jaunty/universe Sources
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://archive.linux.duke.edu jaunty/universe Packages
Get:3 http://ppa.launchpad.net jaunty/main Packages [3089B]
Hit http://archive.linux.duke.edu jaunty/multiverse Packages       
Get:4 http://ppa.launchpad.net jaunty/main Sources [1216B]
Fetched 79.3kB in 3s (20.7kB/s)
Reading package lists... Done
karthick@Learners-desktop:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools keyutils
The following NEW packages will be installed:
  samba smbfs
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 6048kB of archives.
After this operation, 17.4MB of additional disk space will be used.
Err http://archive.linux.duke.edu jaunty/main samba 2:3.3.2-1ubuntu3
  403 Forbidden
Err http://archive.linux.duke.edu jaunty/main smbfs 2:3.3.2-1ubuntu3
  403 Forbidden
Failed to fetch http://archive.linux.duke.edu/ubuntu/pool/main/s/samba/samba_3.3.2-1ubuntu3_i386.deb  403 Forbidden
Failed to fetch http://archive.linux.duke.edu/ubuntu/pool/main/s/samba/smbfs_3.3.2-1ubuntu3_i386.deb  403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by karthick87 on 2010-03-08
I was using proxy,i disabled it...And now i am able to install the package..

---

