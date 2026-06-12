---
title: "updtes manager is gray and does not function"
date: 2009-09-24
forum: General Help
---

### Post by doron387 on 2009-09-24
hey guys,
ubuntu 9.04, synaptic repos updated today, laptop hp pavilion dv6000, when i start the machine, 2-4 minutes after it boots, the update manager pops up and says that some crucial security updates are available.
when i click update, it freezes.
it all started 5 days ago, and i could not update though i have tried few times, 
has sombody else have this problem ? does any body have a clue what is wrong / what should be done ?
thnx
doron387

---

### Post by credobyte on 2009-09-24
Can you upgrade ( update ) your machine via command line ?

```
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by wojox on 2009-09-24
And if it can't post back the errors please.

---

### Post by doron387 on 2009-09-24
it seems that it did update the system, but please have a look in the output as there are some weired messages in it,
also, the update-manager is still grey and won't let me close it (does not respond)

output :
 doron@laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for doron: 
Hit [http://ppa.Launchpad.Net](http://ppa.Launchpad.Net) jaunty Release.gpg                                
Ign [http://ppa.Launchpad.Net](http://ppa.Launchpad.Net) jaunty/main Translation-he                        
Hit [http://ppa.Launchpad.Net](http://ppa.Launchpad.Net) jaunty Release                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-he                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-he               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://ppa.Launchpad.Net](http://ppa.Launchpad.Net) jaunty/main Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/main Translation-he          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/restricted Translation-he              
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/universe Translation-he      
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/multiverse Translation-he    
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates Release.gpg [189B] 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main Translation-he     
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/restricted Translation-he
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/universe Translation-he 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/multiverse Translation-he
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-he   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-he
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-he
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty Release                      
Hit [http://ppa.Launchpad.Net](http://ppa.Launchpad.Net) jaunty/main Sources                               
Get:3 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates Release [49.6kB]   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [103kB]         
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty/multiverse Sources                     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2589B]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [26.6kB]         
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [623B]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [35.9kB]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [7109B]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [1662B]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [588B]    
Get:13 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main Packages [178kB]       
Get:14 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B] 
Get:15 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main Sources [50.6kB]       
Get:16 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/restricted Sources [623B]   
Get:17 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/universe Packages [56.6kB]  
Get:18 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/universe Sources [15.3kB]   
Get:19 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B] 
Get:20 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]  
Fetched 591kB in 27s (21.8kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
&#1492;&#1495;&#1489;&#1497;&#1500;&#1493;&#1514; &#1492;&#1489;&#1488;&#1493;&#1514; &#1497;&#1513;&#1493;&#1491;&#1512;&#1490;&#1493;:
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data libneon27
  libneon27-gnutls libnewt0.52 libpq5 python-newt whiptail
11 &#1502;&#1513;&#1493;&#1491;&#1512;&#1490;&#1497;&#1501;, 0 &#1502;&#1493;&#1514;&#1511;&#1504;&#1497;&#1501; &#1495;&#1491;&#1513;&#1497;&#1501;, 0 &#1497;&#1493;&#1505;&#1512;&#1493; &#1493;-0 &#1500;&#1488; &#1497;&#1513;&#1493;&#1491;&#1512;&#1490;&#1493;.
&#1510;&#1512;&#1497;&#1498; &#1500;&#1511;&#1489;&#1500; 26.5MB &#1502;&#1514;&#1493;&#1498; &#1492;&#1488;&#1512;&#1499;&#1497;&#1493;&#1504;&#1497;&#1501;.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main kdelibs5-data 4:4.2.2-0ubuntu5.2 [1993kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main python-newt 0.52.2-11.3ubuntu3.1 [40.1kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnewt0.52 0.52.2-11.3ubuntu3.1 [58.5kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main whiptail 0.52.2-11.3ubuntu3.1 [35.8kB]
Get:5 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main kdelibs-bin 4:4.2.2-0ubuntu5.2 [269kB]
Get:6 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main kdelibs5 4:4.2.2-0ubuntu5.2 [6783kB]
Get:7 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main kdelibs-data 4:3.5.10.dfsg.1-1ubuntu8.2 [6752kB]
Get:8 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main kdelibs4c2a 4:3.5.10.dfsg.1-1ubuntu8.2 [10.0MB]
Get:9 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main libneon27 0.28.2-6.1ubuntu0.1 [140kB]
Get:10 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main libneon27-gnutls 0.28.2-6.1ubuntu0.1 [115kB]
Get:11 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) jaunty-updates/main libpq5 8.3.8-0ubuntu9.04 [303kB]
Fetched 26.5MB in 10min 57s (40.3kB/s)                                         
(Reading database ... 152076 files and directories currently installed.)
Preparing to replace kdelibs5-data 4:4.2.2-0ubuntu5.1 (using .../kdelibs5-data_4%3a4.2.2-0ubuntu5.2_all.deb) ...
Unpacking replacement kdelibs5-data ...
Preparing to replace kdelibs-bin 4:4.2.2-0ubuntu5.1 (using .../kdelibs-bin_4%3a4.2.2-0ubuntu5.2_i386.deb) ...
Unpacking replacement kdelibs-bin ...
Preparing to replace kdelibs5 4:4.2.2-0ubuntu5.1 (using .../kdelibs5_4%3a4.2.2-0ubuntu5.2_i386.deb) ...
Unpacking replacement kdelibs5 ...
Preparing to replace python-newt 0.52.2-11.3ubuntu3 (using .../python-newt_0.52.2-11.3ubuntu3.1_i386.deb) ...
Unpacking replacement python-newt ...
Preparing to replace libnewt0.52 0.52.2-11.3ubuntu3 (using .../libnewt0.52_0.52.2-11.3ubuntu3.1_i386.deb) ...
Unpacking replacement libnewt0.52 ...
Preparing to replace whiptail 0.52.2-11.3ubuntu3 (using .../whiptail_0.52.2-11.3ubuntu3.1_i386.deb) ...
Unpacking replacement whiptail ...
Preparing to replace kdelibs-data 4:3.5.10.dfsg.1-1ubuntu8.1 (using .../kdelibs-data_4%3a3.5.10.dfsg.1-1ubuntu8.2_all.deb) ...
Unpacking replacement kdelibs-data ...
Preparing to replace kdelibs4c2a 4:3.5.10.dfsg.1-1ubuntu8.1 (using .../kdelibs4c2a_4%3a3.5.10.dfsg.1-1ubuntu8.2_i386.deb) ...
Unpacking replacement kdelibs4c2a ...
Preparing to replace libneon27 0.28.2-6.1 (using .../libneon27_0.28.2-6.1ubuntu0.1_i386.deb) ...
Unpacking replacement libneon27 ...
Preparing to replace libneon27-gnutls 0.28.2-6.1 (using .../libneon27-gnutls_0.28.2-6.1ubuntu0.1_i386.deb) ...
Unpacking replacement libneon27-gnutls ...
Preparing to replace libpq5 8.3.7-1 (using .../libpq5_8.3.8-0ubuntu9.04_i386.deb) ...
Unpacking replacement libpq5 ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up kdelibs5-data (4:4.2.2-0ubuntu5.2) ...

Setting up libnewt0.52 (0.52.2-11.3ubuntu3.1) ...

Setting up python-newt (0.52.2-11.3ubuntu3.1) ...

Setting up whiptail (0.52.2-11.3ubuntu3.1) ...
Setting up kdelibs-data (4:3.5.10.dfsg.1-1ubuntu8.2) ...

Setting up kdelibs4c2a (4:3.5.10.dfsg.1-1ubuntu8.2) ...

Setting up libneon27 (0.28.2-6.1ubuntu0.1) ...

Setting up libneon27-gnutls (0.28.2-6.1ubuntu0.1) ...

Setting up libpq5 (8.3.8-0ubuntu9.04) ...

Setting up kdelibs-bin (4:4.2.2-0ubuntu5.2) ...
Setting up kdelibs5 (4:4.2.2-0ubuntu5.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
doron@laptop:~$

---

