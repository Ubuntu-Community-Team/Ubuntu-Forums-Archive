---
title: "Firefox continually crashing with Ubuntu 10.04"
date: 2011-06-11
forum: General Help
---

### Post by livetobefree on 2011-06-11
I use Firefox, and Firefox has been crashing like crazy on me for the last few weeks.  Does this constant crashing have anything to do with not being able to update from synaptic?

---

### Post by livetobefree on 2011-06-11
I tried to run some code on the terminal to fix it, here what I did, and what I got back:



```
empty@empty-zen:~$ dpkg --clear-avail
dpkg: bulk available update requires write access to dpkg status area
empty@empty-zen:~$ sudo apt-get update
[sudo] password for empty: 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ 
```

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **livetobefree said:**
> I use Firefox, and Firefox has been crashing like crazy on me for the last few weeks.  Does this constant crashing have anything to do with not being able to update from synaptic?

In terminal cut and paste:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable 
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by livetobefree on 2011-06-11
Hello,

 and thanks for the relpy

Ok I ran the first code line and got this;



[B]empty@empty-zen:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
[/B]


then I ran the 2nd and got the same parsed error massage:


[B]empty@empty-zen:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Fetched 31.0kB in 0s (34.4kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


[/B]Any thoughts on how to solve this?

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **livetobefree said:**
> Hello,

 and thanks for the relpy

Ok I ran the first code line and got this;



[B]empty@empty-zen:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
[/B]


then I ran the 2nd and got the same parsed error massage:


[B]empty@empty-zen:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Fetched 31.0kB in 0s (34.4kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


[/B]Any thoughts on how to solve this?

Okay, now this:

```


sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade

```

By the way are you using a hardwired connection to the internet or a WIFI?

---

### Post by livetobefree on 2011-06-11
Hi thanks for getting back to me!

I've ALWAYS updated/upgraded **via Wifi**

and this time I got the same error message,  I've tried a few different things since I posted that so I included all that Ive been up to, here goes, its long and repetitive:

```
empty@empty-zen:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ sudo dpkg-reconfigure locales
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
/usr/sbin/dpkg-reconfigure: locales is not installed
empty@empty-zen:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
empty@empty-zen:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Fetched 31.0kB in 0s (34.4kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ sudo dpkg --configure -a
[sudo] password for empty: 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
empty@empty-zen:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_source_Sources'
empty@empty-zen:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]                        
Get:10 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                     
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                         
Get:12 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.4kB]            
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]                   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [581B]                     
Get:16 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [6,590B]             
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]        
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1,353kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources [640kB]                   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]             
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [194kB]       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [71.5kB]  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [58.2kB]       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [21.3kB]   
Fetched 21.2MB in 43s (491kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ 


```i wont do anything else until I hear back, but I gotta go now I'll check back later.

---

### Post by uRock on 2011-06-11
Please use code tags instead of bold. Just highlight the text then click the ***#*** sign.

---

### Post by linuxinstalledfromhdd on 2011-06-11
Did you try this from terminal:

sudo rm /var/lib/apt/lists/* -vf

I don't know. Maybe sunspots?  Try a hardwire for huge huge updates, like when you do a system installation.  That way you can keep corruption to a minimum.

> **livetobefree said:**
> Hi thanks for getting back to me!

I've ALWAYS updated/upgraded **via Wifi**

and this time I got the same error message,  I've tried a few different things since I posted that so I included all that Ive been up to, here goes, its long and repetitive:

```
empty@empty-zen:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ sudo dpkg-reconfigure locales
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
/usr/sbin/dpkg-reconfigure: locales is not installed
empty@empty-zen:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: public key "Launchpad PPA for Mozilla Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
empty@empty-zen:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Fetched 31.0kB in 0s (34.4kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ sudo dpkg --configure -a
[sudo] password for empty: 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 7893 package 'python-egenix-mxdatetime':
 field name `bdates' must be followed by colon
empty@empty-zen:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_karmic_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_mozillateam_firefox-stable_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_source_Sources'
empty@empty-zen:~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]              
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                    
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]                        
Get:10 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                     
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                         
Get:12 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.4kB]            
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [16.7kB]                   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [581B]                     
Get:16 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [6,590B]             
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]        
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1,353kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources [640kB]                   
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]             
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [194kB]       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [71.5kB]  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [58.2kB]       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [21.3kB]   
Fetched 21.2MB in 43s (491kB/s)                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
empty@empty-zen:~$ 


```i wont do anything else until I hear back, but I gotta go now I'll check back later.

---

### Post by mgmiller on 2011-06-11
You appear to have repositories for both karmic and lucid enabled.  This may be causing some confusion in your system.  You need to remove the karmic entries.
Go into synaptic package manager and click on Settings > Repositories
Go to the "Other Software" tab and look for entries referring to Karmic.  You can then delete them.  Close the window and click the reload button in synaptic.  Hopefully all your error messages will be gone.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **mgmiller said:**
> You appear to have repositories for both karmic and lucid enabled.  This may be causing some confusion in your system.  You need to remove the karmic entries.
Go into synaptic package manager and click on Settings > Repositories
Go to the "Other Software" tab and look for entries referring to Karmic.  You can then delete them.  Close the window and click the reload button in synaptic.  Hopefully all your error messages will be gone.

They added the wrong repositories.

---

### Post by livetobefree on 2011-06-12
hi 

  Yes I run all those commands in terminal.  But Icouldn't even access the synaptic package manager AT ALL, so I opened the other software option just above it thru System/Administrative/Other Software and deleted the Karmic repositories from there.  But I'm getting into worse trouble it seems, now I get a blank box when I try Synaptic and a BLANK BOX WHEN I try to OPEN TERMINAL !!!  oh no!   

Things got worse maybe I shouldnt have deleted the karmic files under other software?  Perhaps somehow my system was co dependent on both?  If possible?  

Firefox still crashes alot, and I cant open any synaptic related thing.  Not even the Terminal as I mentioned before, its becoming sort of a crisis!  yikes!

---

### Post by livetobefree on 2011-06-12
I tried to go to the Synaptic Package Manager and..............I couldnt even access it!   

this is what I got back.....


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.




is there any way to remove the old repositories from terminal?

---

### Post by mgmiller on 2011-06-13
I believe you have some really incorrect settings in your sources.list.  You should never have 2 different releases listed for the main OS sources.  

Could you go to /etc/apt with the file browser and _right click_ the file sources.list and then open it with gedit.

Copy & paste the contents here.

Once I am happy with the contents, there are some commands I will have you run to do a dist-upgrade that hopefully will get you back up and running.

---

### Post by NetworkEngineer on 2011-06-13
I had the same problem, but I am running on 11.04 Natty.  It started when a recent update upgraded from FF 4.0.1 to 5.0.  I would launch FF and within about 10 seconds it would crash.  Tried launching in safe mode, same thing. Disabled all add-ons and tried running in safe mode, same problem.  Had to check /var/cache/apt/archives/ to see which packages were recently upgraded, then used Synaptic Package Manager to downgrade (and for one of them, remove) those packages.

The following were the culprit packages (for me) listed in that directory:
[FONT="Courier New"](downgraded to 4.0.1) firefox_5.0~b5+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb
(downgraded to 4.0.1) firefox-branding_5.0~b5+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb
(downgraded to 4.0.1) firefox-globalmenu_5.0~b5+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb
(downgraded to 4.0.1) firefox-gnome-support_5.0~b5+build1+nobinonly-0ubuntu0.11.04.1_amd64.deb
(removed) firefox-locale-en_5.0~b5+build1+nobinonly-0ubuntu0.11.04.1_all.deb[/FONT]

To back out the updates, I did a search for "firefox" in Synaptic Package Manager.  I went down the results, and for each one above that needed to be down graded, I clicked on the item, and selected Force Version... from the Package menu, then selected the previous 4.0.1 equivalent in the resulting dialog box.  Since the "firefox-locale-en_5.0~..." didn't have a 4.0.1 equivalent to downgrade to, I chose to remove it.

After doing so I was able to launch and use FF again, and after re-enabling everything under Extensions, Appearance and Plug-Ins, I was fully back in business.

---

### Post by FormatSeize on 2011-06-13
> **livetobefree said:**
> is there any way to remove the old repositories from terminal?
```
sudo nano /etc/apt/sources.list
```

---

