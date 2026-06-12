---
title: "I can't update my application with the update manager... Help"
date: 2010-12-07
forum: General Help
---

### Post by q8.legend on 2010-12-07
Hi Guys...

I have problem when i try to update my application using the update manager...

this is the message that shown to me, when i try to update...

The action would require the installation of packages from not authenticated sources:

apport apport-gtk software-center

what can i do to fix that problem ??

Thanks alot...

---

### Post by sikander3786 on 2010-12-07
There might be some GPG (digital signature) key issue. Post the complete output of this command from Applications > Accessories > Terminal.

```
sudo apt-get update
```

---

### Post by q8.legend on 2010-12-07
This is the output...

```
Hit http://extras.ubuntu.com maverick Release.gpg
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://download.virtualbox.org maverick Release.gpg                        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en             
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_US          
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Get:2 http://dl.google.com stable Release [2,544B]                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Get:3 http://dl.google.com stable/non-free amd64 Packages [1,025B]             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_US
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Hit http://download.virtualbox.org maverick Release                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://download.virtualbox.org maverick/non-free amd64 Packages            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg      
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Hit http://packages.medibuntu.org maverick Release                   
Hit http://packages.medibuntu.org maverick/free Sources              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Hit http://packages.medibuntu.org maverick/non-free Sources          
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en
Hit http://packages.medibuntu.org maverick/free amd64 Packages                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                    
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en 
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:5 http://us.archive.ubuntu.com maverick-proposed Release.gpg [198B]    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick Release
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick-backports Release                    
Hit http://us.archive.ubuntu.com maverick-security Release                     
Get:6 http://us.archive.ubuntu.com maverick-proposed Release [31.4kB]          
Ign http://us.archive.ubuntu.com maverick-proposed Release                     
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/main Sources
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick/universe Sources                 
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages          
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-backports/main amd64 Packages        
Hit http://us.archive.ubuntu.com maverick-backports/universe amd64 Packages    
Hit http://us.archive.ubuntu.com maverick-security/main Sources                
Hit http://us.archive.ubuntu.com maverick-security/universe Sources            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-security/main amd64 Packages         
Hit http://us.archive.ubuntu.com maverick-security/universe amd64 Packages     
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages/DiffIndex
Hit http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages         
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages     
Hit http://ppa.launchpad.net maverick Release                                  
Get:7 http://ppa.launchpad.net maverick Release [39.8kB]                       
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex            
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Fetched 4,274B in 10s (389B/s)                                                 
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 4D17133CFC5D50C5 Launchpad elementaryart

```

---

### Post by karthick87 on 2010-12-07
Type the following in terminal,

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update 
``````
sudo apt-get update
```

---

### Post by q8.legend on 2010-12-07
> **karthick87 said:**
> Type the following in terminal,

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
``````
sudo apt-get update
```

It doesn't fix the problem :(

This is the output
```

Hit http://us.archive.ubuntu.com maverick Release.gpg                           
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]                       
Hit http://ppa.launchpad.net maverick Release.gpg                               
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en               
Hit http://packages.medibuntu.org maverick Release.gpg                          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en           
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en
Get:2 http://dl.google.com stable Release.gpg [189B]                            
Hit http://extras.ubuntu.com maverick Release                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en       
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main amd64 Packages                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US    
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en              
Ign http://packages.medibuntu.org/ maverick/free Translation-en                 
Hit http://ppa.launchpad.net maverick Release.gpg                               
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                   
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US              
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en   
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_US           
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://download.virtualbox.org maverick Release.gpg                         
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg                 
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://packages.medibuntu.org maverick Release                              
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Hit http://ppa.launchpad.net maverick Release.gpg                               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en 
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_US
Hit http://packages.medibuntu.org maverick/free Sources                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en
Hit http://download.virtualbox.org maverick Release                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Hit http://packages.medibuntu.org maverick/non-free Sources                     
Hit http://download.virtualbox.org maverick/non-free amd64 Packages             
Hit http://us.archive.ubuntu.com maverick-security Release.gpg                  
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en
Hit http://packages.medibuntu.org maverick/free amd64 Packages                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Get:3 http://us.archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US
Get:4 http://dl.google.com stable Release [2,544B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Get:6 http://dl.google.com stable/non-free amd64 Packages [1,025B]   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                       
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release                       
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick-backports Release                    
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick-security Release
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Get:7 http://us.archive.ubuntu.com maverick-proposed Release [31.4kB]           
Ign http://us.archive.ubuntu.com maverick-proposed Release                      
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick/main Sources                          
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Hit http://us.archive.ubuntu.com maverick/universe Sources                      
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en 
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages                   
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                               
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages               
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en 
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                  
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources              
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages           
Hit http://ppa.launchpad.net maverick Release                                   
Get:8 http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages [60.1kB]
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://us.archive.ubuntu.com maverick-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com maverick-backports/universe amd64 Packages     
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://us.archive.ubuntu.com maverick-security/main Sources                 
Get:9 http://ppa.launchpad.net maverick Release [39.8kB]                        
Hit http://ppa.launchpad.net maverick Release                                   
Get:10 http://us.archive.ubuntu.com maverick-security/universe Sources [4,985B] 
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://us.archive.ubuntu.com maverick-security/main amd64 Packages          
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://us.archive.ubuntu.com maverick-security/universe amd64 Packages      
Hit http://ppa.launchpad.net maverick Release                                   
Hit http://ppa.launchpad.net maverick/main Sources                              
Ign http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Ign http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net maverick/main Sources                              
Get:11 http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages [24.5kB]
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Get:12 http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages [23.6kB]
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Get:13 http://ppa.launchpad.net maverick/main Sources [612B]                    
Get:14 http://ppa.launchpad.net maverick/main amd64 Packages [573B]             
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                              
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                       
Fetched 119kB in 15s (7,545B/s)                                                 
W: GPG error: http://us.archive.ubuntu.com maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ maverick/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_maverick_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_maverick_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_main_binary-amd64_Packages)

q8_legend@Q8:~$ sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en
Hit http://download.virtualbox.org maverick Release.gpg                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://ppa.launchpad.net/banshee-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en             
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Hit http://download.virtualbox.org maverick Release                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_US          
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://download.virtualbox.org maverick/non-free amd64 Packages            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg                
Get:2 http://dl.google.com stable Release [2,544B]                             
Hit http://packages.medibuntu.org maverick Release                             
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/deluge-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Hit http://packages.medibuntu.org maverick/free Sources                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Get:3 http://dl.google.com stable/non-free amd64 Packages [1,025B]             
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://packages.medibuntu.org maverick/non-free Sources
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg                 
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en
Hit http://packages.medibuntu.org maverick/free amd64 Packages                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://packages.medibuntu.org maverick/non-free amd64 Packages
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com maverick-proposed Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Ign http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Hit http://us.archive.ubuntu.com maverick-backports Release                   
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                             
Hit http://us.archive.ubuntu.com maverick-security Release
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en
Get:5 http://us.archive.ubuntu.com maverick-proposed Release [31.4kB]         
Ign http://us.archive.ubuntu.com maverick-proposed Release             
Ign http://ppa.launchpad.net/tillux/t-misc/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick/universe Sources                     
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick/main amd64 Packages                  
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://us.archive.ubuntu.com maverick/universe amd64 Packages              
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://us.archive.ubuntu.com maverick-updates/main amd64 Packages          
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://us.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Hit http://us.archive.ubuntu.com maverick-backports/main amd64 Packages        
Hit http://us.archive.ubuntu.com maverick-backports/universe amd64 Packages    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-security/main Sources                
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://us.archive.ubuntu.com maverick-security/universe Sources            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://us.archive.ubuntu.com maverick-security/main amd64 Packages         
Hit http://ppa.launchpad.net maverick Release                                 
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://us.archive.ubuntu.com maverick-security/universe amd64 Packages 
Hit http://ppa.launchpad.net maverick/main amd64 Packages                     
Hit http://ppa.launchpad.net maverick/main Sources                            
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                  
Hit http://ppa.launchpad.net maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main amd64 Packages                  
Hit http://ppa.launchpad.net maverick/main amd64 Packages                  
Ign http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Ign http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://us.archive.ubuntu.com maverick-proposed/main amd64 Packages         
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://us.archive.ubuntu.com maverick-proposed/universe amd64 Packages     
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                      
Fetched 3,957B in 10s (371B/s)                                                 
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


```

---

### Post by q8.legend on 2010-12-07
any solution ???

---

### Post by sikander3786 on 2010-12-07
Go to Software Center > Edit > Software Sources > Authentication and click the 'Restore Defaults' button and try apt-get update again.

If that doesn't solve the issue, delete the key **40976EAF437D05B5** from Software Sources and add it using this command.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

### Post by karthick87 on 2010-12-07
```
sudo apt-key del 40976EAF437D05B5
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
```
sudo apt-get update
```

---

### Post by q8.legend on 2010-12-08
Thank u soooo much "[karthick87]("http://ubuntuforums.org/member.php?u=891422")" & "sikander3786"

The solution that u did provided to me works great...

Thans alot guys ;)

---

