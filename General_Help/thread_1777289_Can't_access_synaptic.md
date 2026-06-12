---
title: "Can't access synaptic"
date: 2011-06-07
forum: General Help
---

### Post by eric948470 on 2011-06-07
Hi,

I just installed Ubuntu 11.04 in my new netbook. I ran synaptic once, and pressed the refresh button. But while the package list was being downloaded, I tried to moved to a better location to get a better wifi signal, and my connection quit.

I tried again, but this time I had logged in to a network that had no Internet connection automatically. I tried downloading the package list again, before realizing I was logged on to the wrong network.

I logged on the correct network and tried again. Synaptic gives me the following message. There is not way through this. When I close the message synaptic quits.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

What's going on? How can I fix this?

Thanks.

---

### Post by sanguinoso on 2011-06-07
Can you run from a terminal.```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and post the error message here?

---

### Post by Rubi1200 on 2011-06-07
Hi and welcome to the forums eric948470 :)

If the commands suggested by sanguinoso don't get you further, then try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Let us know what works and if you require additional assistance with anything.

---

### Post by eric948470 on 2011-06-07
Here's the output for sudo apt-get update

```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get update
[sudo] password for eric948470: 
Ign http://extras.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease                       
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                       
Get:2 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:3 http://security.ubuntu.com natty-security Release [27.2 kB]              
Get:4 http://extras.ubuntu.com natty Release [9,753 B]                         
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                      
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en       
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com natty-security/restricted Translation-en       
Ign http://security.ubuntu.com natty-security/universe Translation-en_US      
Ign http://security.ubuntu.com natty-security/universe Translation-en         
Ign http://extras.ubuntu.com natty/main Translation-en_US                     
Ign http://extras.ubuntu.com natty/main Translation-en                        
Ign http://us.archive.ubuntu.com natty InRelease        
Ign http://us.archive.ubuntu.com natty-updates InRelease
Get:5 http://us.archive.ubuntu.com natty Release.gpg [198 B]
Get:6 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]
Get:7 http://us.archive.ubuntu.com natty Release [39.8 kB]
Get:8 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 105 kB in 8s (12.3 kB/s)                                               
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
eric948470@eric948470-N150P-N210P-N220P:~$
```Here's the ouptput from sudo apt-get upgrade
```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
eric948470@eric948470-N150P-N210P-N220P:~$ 

```Here's the output for
sudo rm var/lib/apt/lists/* -vf
sudo apt-get update

```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://extras.ubuntu.com natty InRelease   
Ign http://security.ubuntu.com natty-security InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Get:2 http://us.archive.ubuntu.com natty Release.gpg [198 B]                  
Get:3 http://security.ubuntu.com natty-security Release.gpg [198 B]
Get:4 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Get:5 http://extras.ubuntu.com natty Release [9,753 B]                         
Get:6 http://security.ubuntu.com natty-security Release [27.2 kB]
Get:7 http://us.archive.ubuntu.com natty Release [39.8 kB]                     
Get:8 http://extras.ubuntu.com natty/main Sources [14 B]                       
Get:9 http://extras.ubuntu.com natty/main i386 Packages [14 B]                 
Get:10 http://security.ubuntu.com natty-security/main Sources [10.8 kB]    
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:11 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]            
Get:12 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:13 http://security.ubuntu.com natty-security/universe Sources [3,152 B]    
Get:14 http://security.ubuntu.com natty-security/multiverse Sources [656 B]    
Get:15 http://us.archive.ubuntu.com natty/main Sources [862 kB]                
Get:16 http://security.ubuntu.com natty-security/main i386 Packages [32.9 kB]  
Get:17 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Get:18 http://security.ubuntu.com natty-security/universe i386 Packages [12.4 kB]
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:19 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,069 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Get:20 http://us.archive.ubuntu.com natty/restricted Sources [4,104 B]
Get:21 http://us.archive.ubuntu.com natty/universe Sources [4,380 kB]
Get:22 http://us.archive.ubuntu.com natty/multiverse Sources [155 kB]          
Get:23 http://us.archive.ubuntu.com natty/main i386 Packages [1,550 kB]        
Get:24 http://us.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]   
Get:25 http://us.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]    
Get:26 http://us.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]    
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:27 http://us.archive.ubuntu.com natty-updates/main Sources [37.9 kB]       
Get:28 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:29 http://us.archive.ubuntu.com natty-updates/universe Sources [9,682 B]   
Get:30 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,378 B] 
Get:31 http://us.archive.ubuntu.com natty-updates/main i386 Packages [124 kB]  
Get:32 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:33 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [45.6 kB]
Get:34 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [3,750 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 13.6 MB in 1min 9s (196 kB/s)                                          
Reading package lists... Done
eric948470@eric948470-N150P-N210P-N220P:~$ 

```Immediately after that the "auto update(?)" appeared and said that there were updates available.

Synaptic works now.

Thanks a lot!

---

### Post by linuxinstalledfromhdd on 2011-06-07
> **eric948470 said:**
> Here's the output for sudo apt-get update

```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get update
[sudo] password for eric948470: 
Ign http://extras.ubuntu.com natty InRelease
Ign http://security.ubuntu.com natty-security InRelease                       
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                       
Get:2 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:3 http://security.ubuntu.com natty-security Release [27.2 kB]              
Get:4 http://extras.ubuntu.com natty Release [9,753 B]                         
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://extras.ubuntu.com natty/main i386 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                      
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com natty-security/multiverse Translation-en       
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com natty-security/restricted Translation-en       
Ign http://security.ubuntu.com natty-security/universe Translation-en_US      
Ign http://security.ubuntu.com natty-security/universe Translation-en         
Ign http://extras.ubuntu.com natty/main Translation-en_US                     
Ign http://extras.ubuntu.com natty/main Translation-en                        
Ign http://us.archive.ubuntu.com natty InRelease        
Ign http://us.archive.ubuntu.com natty-updates InRelease
Get:5 http://us.archive.ubuntu.com natty Release.gpg [198 B]
Get:6 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]
Get:7 http://us.archive.ubuntu.com natty Release [39.8 kB]
Get:8 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 105 kB in 8s (12.3 kB/s)                                               
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
eric948470@eric948470-N150P-N210P-N220P:~$
```Here's the ouptput from sudo apt-get upgrade
```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
eric948470@eric948470-N150P-N210P-N220P:~$ 

```Here's the output for
sudo rm var/lib/apt/lists/* -vf
sudo apt-get update

```
eric948470@eric948470-N150P-N210P-N220P:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
eric948470@eric948470-N150P-N210P-N220P:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Ign http://extras.ubuntu.com natty InRelease   
Ign http://security.ubuntu.com natty-security InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Get:2 http://us.archive.ubuntu.com natty Release.gpg [198 B]                  
Get:3 http://security.ubuntu.com natty-security Release.gpg [198 B]
Get:4 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Get:5 http://extras.ubuntu.com natty Release [9,753 B]                         
Get:6 http://security.ubuntu.com natty-security Release [27.2 kB]
Get:7 http://us.archive.ubuntu.com natty Release [39.8 kB]                     
Get:8 http://extras.ubuntu.com natty/main Sources [14 B]                       
Get:9 http://extras.ubuntu.com natty/main i386 Packages [14 B]                 
Get:10 http://security.ubuntu.com natty-security/main Sources [10.8 kB]    
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Get:11 http://us.archive.ubuntu.com natty-updates Release [27.2 kB]            
Get:12 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:13 http://security.ubuntu.com natty-security/universe Sources [3,152 B]    
Get:14 http://security.ubuntu.com natty-security/multiverse Sources [656 B]    
Get:15 http://us.archive.ubuntu.com natty/main Sources [862 kB]                
Get:16 http://security.ubuntu.com natty-security/main i386 Packages [32.9 kB]  
Get:17 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Get:18 http://security.ubuntu.com natty-security/universe i386 Packages [12.4 kB]
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:19 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,069 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Get:20 http://us.archive.ubuntu.com natty/restricted Sources [4,104 B]
Get:21 http://us.archive.ubuntu.com natty/universe Sources [4,380 kB]
Get:22 http://us.archive.ubuntu.com natty/multiverse Sources [155 kB]          
Get:23 http://us.archive.ubuntu.com natty/main i386 Packages [1,550 kB]        
Get:24 http://us.archive.ubuntu.com natty/restricted i386 Packages [8,986 B]   
Get:25 http://us.archive.ubuntu.com natty/universe i386 Packages [6,021 kB]    
Get:26 http://us.archive.ubuntu.com natty/multiverse i386 Packages [183 kB]    
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:27 http://us.archive.ubuntu.com natty-updates/main Sources [37.9 kB]       
Get:28 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:29 http://us.archive.ubuntu.com natty-updates/universe Sources [9,682 B]   
Get:30 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,378 B] 
Get:31 http://us.archive.ubuntu.com natty-updates/main i386 Packages [124 kB]  
Get:32 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:33 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [45.6 kB]
Get:34 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [3,750 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 13.6 MB in 1min 9s (196 kB/s)                                          
Reading package lists... Done
eric948470@eric948470-N150P-N210P-N220P:~$ 

```Immediately after that the "auto update(?)" appeared and said that there were updates available.

Synaptic works now.

Thanks a lot!

I recommend using a hard-wired connection at least until you can get your system fully updated immediately after a fresh installation.  You don't want to risk borking your entire system because you used wifi to intially get everything perfect.  It's just one more thing that can go wrong that you can avoid with a simple ethernet cable for about 30 minutes of hard-wired use.

---

### Post by sanjiv856 on 2011-06-07
I had the similar issues, 

sudo rm /var/lib/apt/lists/* -vf command helped after fresh installation 

Thanks for posting.

---

### Post by Rubi1200 on 2011-06-07
@eric948470 & sanjiv856

Glad this worked for both of you.

Enjoy :-)

eric948470, please mark this thread Solved using the Thread Tools near the top of the page so others can also find a working solution.

Thanks.

---

### Post by chinnnaz on 2011-06-29
Boss..........U rockssssss.!! It workzzzzzzzzzzzz.........>!!

---

### Post by Rubi1200 on 2011-06-29
Hi and welcome to the forums chinnnaz :)

You're more than welcome; I am glad you too found a solution.

---

### Post by basilarchia on 2011-07-06
This is a really serious problem. This can happen to any arbitrary user that might cancel, kill, reboot, etc while apt-get update is running.

The package management system definitely needs to be smart enough to purge the lists and re-download them. IMHO this bug should be marked 'critical'.

---

### Post by brons2 on 2011-07-07
> **Rubi1200 said:**
> Hi and welcome to the forums eric948470 :)

If the commands suggested by sanguinoso don't get you further, then try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```Let us know what works and if you require additional assistance with anything.

I had the same problems and this fixed it for me as well.  Thanks!!

---

### Post by Rubi1200 on 2011-07-08
Hi brons2,
glad this worked for you too :-)

---

### Post by tburnett80 on 2013-02-01
I have tried the 

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update


and I keep getting the same error:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.


Any Ideas?

---

