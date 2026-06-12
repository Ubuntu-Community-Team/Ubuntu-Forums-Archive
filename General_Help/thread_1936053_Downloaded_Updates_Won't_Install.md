---
title: "Downloaded Updates Won't Install"
date: 2012-03-05
forum: General Help
---

### Post by gdawg on 2012-03-05
The Update Manager showed approximately 74MB to download. I downloaded via Update Mgr. and it's hanging on install. Nothing is installing and I can't close Update Mgr. screen.(Selecting the X has no effect).Here is output of 'sudo apt-update':
```

ane@daisy > ~ $ sudo apt-get update
[sudo] password for jane: 
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Hit http://linux.dropbox.com lucid Release                                     
Hit http://linux.dropbox.com lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.getdeb.net lucid-getdeb Release.gpg                         
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_US      
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid-security Release.gpg                    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid Release                                 
Hit http://badgerports.org lucid Release.gpg                                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid-security Release                        
Hit http://archive.getdeb.net lucid-getdeb Release                             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://badgerports.org/ lucid/main Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://archive.getdeb.net lucid-getdeb/apps Packages                       
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com lucid-security/main Packages              
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
Hit http://badgerports.org lucid Release
Hit http://badgerports.org lucid/main Packages
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```I previously was trying to solve a problem with Ubuntu not shutting down properly.
Any help will be appreciated.
Linux daisy 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
Running win 7 with numerous Linux distros. on a Dell Inspiron 530S Desktop on 2 hard drives.

---

### Post by seawolf167 on 2012-03-05
> **gdawg said:**
> The Update Manager showed approximately 74MB to download. I downloaded via Update Mgr. and it's hanging on install. Nothing is installing and I can't close Update Mgr. screen.(Selecting the X has no effect).Here is output of 'sudo apt-update':
```

ane@daisy > ~ $ sudo apt-get update
[sudo] password for jane: 
...
[B]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

```

Do you have the Synaptic Package Manager open? The Ubuntu Software Center? Try closing those since you can only have one running updates/installations/etc. at a time, then re-run your command

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gdawg on 2012-03-05
Yes Synaptic Pkg. Mgr. is open and it won't close. The 'Applying Changes' 'Installing Software' window is stuck and also won't close. None of the downloaded updates are being installed. It's stuck unpacking 'replacement chromium-codecs-ffmpeg ...'

---

### Post by seawolf167 on 2012-03-05
You can force kill synaptic by finding the process ID with the following command

```
ps -ef | grep -i synaptic
```

then kill them with

```
kill process_id
```

---

### Post by gdawg on 2012-03-05
> **seawolf167 said:**
> You can force kill synaptic by finding the process ID with the following command

```
ps -ef | grep -i synaptic
```

then kill them with

```
kill process_id
```
Thanks seawolf167. I'll get right on it and will get back with results.

---

### Post by gdawg on 2012-03-05
Here are the results of suggested commands:
jane@daisy > ~ $ ps -ef | grep -i synaptic
jane      1920  1877  0 13:07 pts/0    00:00:00 grep --color=auto -i synaptic
jane@daisy > ~ $ kill process_id
bash: kill: process_id: arguments must be process or job IDs
jane@daisy > ~ $ kill 1920
bash: kill: (1920) - No such process
jane@daisy > ~ $ sudo kill 1920
[sudo] password for jane: 
kill: No such process
jane@daisy > ~ $ kill 1877
jane@daisy > ~ $ 
jane@daisy > ~ $ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:1 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg [836B]                
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:4 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release [7,252B]                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://badgerports.org](http://badgerports.org) lucid Release.gpg                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [57.3kB]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://badgerports.org/](http://badgerports.org/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [573kB]
Hit [http://badgerports.org](http://badgerports.org) lucid Release                                      
Hit [http://badgerports.org](http://badgerports.org) lucid/main Packages                                
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,994B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [215kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,834B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [254kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [92.8kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,057B]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [382kB]       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages [14B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [118kB]        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources [14B]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [117kB]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [34.8kB]   
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages [4,561B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources [1,760B] 
Fetched 1,937kB in 8s (217kB/s)                                                
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
jane@daisy > ~ $ sudo dpkg --configure -a
jane@daisy > ~ $ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US      
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://badgerports.org](http://badgerports.org) lucid Release.gpg                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://badgerports.org/](http://badgerports.org/) lucid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources
Hit [http://badgerports.org](http://badgerports.org) lucid Release             
Hit [http://badgerports.org](http://badgerports.org) lucid/main Packages       
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
jane@daisy > ~ $ sudo apt-get update
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ kubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/main Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ natty/restricted Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/ xubuntu/dists/natty/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://badgerports.org](http://badgerports.org) lucid Release.gpg                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources
Ign [http://badgerports.org/](http://badgerports.org/) lucid/main Translation-en_US
Hit [http://badgerports.org](http://badgerports.org) lucid Release
Hit [http://badgerports.org](http://badgerports.org) lucid/main Packages
Reading package lists... Done
jane@daisy > ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
3 upgraded, 0 newly installed, 0 to remove and 181 not upgraded.
2 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 541kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226486 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 16.0.912.77~r118311-0ubuntu0.10.04.1 (using .../chromium-codecs-ffmpeg_17.0.963.56~r121963-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...

It's stuck once again trying to unpack and install. I appreciate your help.

---

### Post by seawolf167 on 2012-03-05
> **gdawg said:**
> 
...
[B]You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f[/B]
...

Try these commands:

```
sudo su
kill 'ps -ef | grep -i synaptic'
apt-get -f install
apt-get update
apt-get upgrade
exit
```

---

### Post by gdawg on 2012-03-05
Here are results of commands(it hung-up during 'apt-get -f install') I waited at least 5 minutes for 'unpacking  replacement ...':
jane@daisy > ~ $ sudo su
[sudo] password for jane: 
root@daisy:/home/jane# kill 'ps -ef | grep -i synaptic'
bash: kill: ps -ef | grep -i synaptic: arguments must be process or job IDs
root@daisy:/home/jane# apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@daisy:/home/jane# sudo dpkg --configure -a
root@daisy:/home/jane# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
3 upgraded, 0 newly installed, 0 to remove and 181 not upgraded.
2 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 541kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226486 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 16.0.912.77~r118311-0ubuntu0.10.04.1 (using .../chromium-codecs-ffmpeg_17.0.963.56~r121963-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...
I'll try again and select 'n' instead of 'y' when asked if I want to continue.

---

### Post by HiImTye on 2012-03-05
try
```
sudo apt-get autoclean && sudo apt-get update && sudo apt-get upgrade
```otherwise you should try removing the packages and reinstalling them
```
 sudo apt-get remove chromium-codecs-ffmpeg && sudo apt-get upgrade
```it'll then list another offending package, repeat with the new package, then install them again:
```
 sudo apt-get install chromium-codecs-ffmpeg other_package_name
```

---

### Post by gdawg on 2012-03-05
After suggested commands the 'chromium-codecs-ffmpeg' is still hung-up unpacking. Following are results:jane@daisy > ~ $ sudo apt-get remove chromium-codecs-ffmpeg && sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  chromium-browser: Depends: chromium-codecs-ffmpeg (>= 0.6) but it is not going to be installed or
                             chromium-codecs-ffmpeg-extra (>= 0.6) but it is not going to be installed
  chromium-browser-l10n: Depends: chromium-browser (= 17.0.963.65~r124586-0ubuntu0.10.04.1) but 16.0.912.77~r118311-0ubuntu0.10.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jane@daisy > ~ $ sudo apt-get remove chromium-browser-l10n && sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-codecs-ffmpeg
The following packages will be REMOVED:
  chromium-browser-l10n
The following packages will be upgraded:
  chromium-codecs-ffmpeg
1 upgraded, 0 newly installed, 1 to remove and 182 not upgraded.
2 not fully installed or removed.
Need to get 0B/386kB of archives.
After this operation, 12.7MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
jane@daisy > ~ $ sudo apt-get remove chromium-browser-l10n && sudo apt-get remove chromium-codecs-ffmpeg && sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-codecs-ffmpeg
The following packages will be REMOVED:
  chromium-browser-l10n
The following packages will be upgraded:
  chromium-codecs-ffmpeg
1 upgraded, 0 newly installed, 1 to remove and 182 not upgraded.
2 not fully installed or removed.
Need to get 0B/386kB of archives.
After this operation, 12.7MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing chromium-browser-l10n (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 chromium-browser-l10n
E: Sub-process /usr/bin/dpkg returned an error code (1)
jane@daisy > ~ $ sudo apt-get install chromium-browser-l10n
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  chromium-browser-l10n: Depends: chromium-browser (= 17.0.963.65~r124586-0ubuntu0.10.04.1) but 16.0.912.77~r118311-0ubuntu0.10.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jane@daisy > ~ $ sudo apt-get remove chromium-browser-l10n
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-codecs-ffmpeg
The following packages will be REMOVED:
  chromium-browser-l10n
The following packages will be upgraded:
  chromium-codecs-ffmpeg
1 upgraded, 0 newly installed, 1 to remove and 182 not upgraded.
2 not fully installed or removed.
Need to get 0B/386kB of archives.
After this operation, 12.7MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing chromium-browser-l10n (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 chromium-browser-l10n
E: Sub-process /usr/bin/dpkg returned an error code (1)
jane@daisy > ~ $ sudo apt-get install chromium-codecs-ffmpeg && sudo apt-get install chromium-browser-l10n
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  chromium-browser-l10n: Depends: chromium-browser (= 17.0.963.65~r124586-0ubuntu0.10.04.1) but 16.0.912.77~r118311-0ubuntu0.10.04.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jane@daisy > ~ $ sudo apt-get install chromium-browser (= 17.0.963.65~r124586-0ubuntu0.10.04.1)
bash: syntax error near unexpected token `('
jane@daisy > ~ $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
3 upgraded, 0 newly installed, 0 to remove and 181 not upgraded.
2 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 561kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 226486 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 16.0.912.77~r118311-0ubuntu0.10.04.1 (using .../chromium-codecs-ffmpeg_17.0.963.65~r124586-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...


Thanks for your response.

---

### Post by sammiev on 2012-03-05
Looks like it's wants to update from the CD-Rom. I think and likely can be wrong but think they check marked CD-Rom updates in the resp.

---

### Post by kevdog on 2012-03-05
I'm wondering if deleting the offending file from the /var/cache/apt/archives folder prior to installation would help.  Just a thought.

---

### Post by iiiears on 2012-03-05
you might just be able to rename the .lock file  Haven done this so back it up.

---

### Post by HiImTye on 2012-03-06
I would give [step 5]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5") a try

---

### Post by gdawg on 2012-03-06
Here are the results of trying step 5:
jane@daisy > ~ $ sudo fuser -vvv /var/lib/dpkg/lock
[sudo] password for jane: 
jane@daisy > ~ $ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
jane@daisy > ~ $ uname -a
Linux daisy 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
jane@daisy > ~ $ sudo rm /var/lib/apt/lists/lock 
jane@daisy > ~ $ sudo rm /var/lib/apt/lists/lock 
rm: cannot remove `/var/lib/apt/lists/lock': No such file or directory
jane@daisy > ~ $ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
jane@daisy > ~ $ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
jane@daisy > ~ $ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
jane@daisy > ~ $ sudo rm -rf /var/lib/dpkg/updates/*
jane@daisy > ~ $ sudo rm -rf /var/lib/apt/lists
jane@daisy > ~ $ sudo rm /var/cache/apt/*.bin
jane@daisy > ~ $ sudo mkdir /var/lib/apt/lists
jane@daisy > ~ $ sudo mkdir /var/lib/apt/lists/partial
jane@daisy > ~ $ LANG=C;sudo apt-get clean
jane@daisy > ~ $ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jane@daisy > ~ $ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package chromium-browser-l10n needs to be reinstalled, but I can't find an archive for it.
jane@daisy > ~ $ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty Release.gpg       
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty Release           
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Packages     
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Packages     
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Packages
Ign cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Packages
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) kubuntu/dists/natty/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/main Packages     
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) natty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1) xubuntu/dists/natty/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg [489B]                                      
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release [2599B]                                         
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages [782B]                                    
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                                  
Get:5 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg [836B]                              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                                  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]                          
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]                         
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                                      
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                                     
Get:11 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8215B]                                    
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                                   
Get:13 [http://badgerports.org](http://badgerports.org) lucid Release.gpg [490B]                                       
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                                       
Get:15 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release [7252B]                                
Get:16 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.6kB]                          
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                                       
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]                           
Get:19 [http://badgerports.org](http://badgerports.org) lucid Release [6123B]                                          
Get:20 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages [89.8kB]                         
Get:21 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources [6690B]                            
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [10.7kB]                                 
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [581B]                                   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [57.3kB]                          
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1386kB]                             
Get:26 [http://badgerports.org](http://badgerports.org) lucid/main Packages [28.8kB]                                   
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6208B]                        
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                               
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3775B]                         
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5448kB]                         
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3165kB]                          
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]                        
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]                         
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [572kB]                      
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3994B]                
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [215kB]                       
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1834B]                 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [255kB]                  
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [93.1kB]                  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5066B]                 
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [382kB]                     
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages [14B]                 
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [118kB]                      
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources [14B]                  
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [117kB]                 
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [34.8kB]                 
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages [4572B]               
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources [1768B]                
Fetched 13.2MB in 51s (256kB/s)                                                              
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/kubuntu/dists/natty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/kubuntu/dists/natty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/xubuntu/dists/natty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/xubuntu/dists/natty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
jane@daisy > ~ $ sudo dpkg --configure -a
jane@daisy > ~ $ sudo dpkg --clear-avail
jane@daisy > ~ $ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg
3 upgraded, 0 newly installed, 0 to remove and 181 not upgraded.
2 not fully installed or removed.
Need to get 20.9MB of archives.
After this operation, 561kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-codecs-ffmpeg 17.0.963.65~r124586-0ubuntu0.10.04.1 [386kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser-l10n 17.0.963.65~r124586-0ubuntu0.10.04.1 [2026kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe chromium-browser 17.0.963.65~r124586-0ubuntu0.10.04.1 [18.5MB]
Fetched 20.9MB in 1min 32s (225kB/s)                                                         
(Reading database ... 226486 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 16.0.912.77~r118311-0ubuntu0.10.04.1 (using .../chromium-codecs-ffmpeg_17.0.963.65~r124586-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...


It's still hanging-up in same place. I waited 10 minutes for it to complete unpacking. Thanks to all for your help.
Forgot to mention that neither Ubuntu nor Mint are shutting down properly. I have to use computer's power button to shut them down. Some of the text from Ubuntu shutdown states "Checking for running unattended-upgrades:". I have no upgrade problems in Mint. Just won't shutdown properly. Don't know if problems are related or not.

---

