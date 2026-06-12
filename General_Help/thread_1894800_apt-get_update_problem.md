---
title: "apt-get update problem"
date: 2011-12-13
forum: General Help
---

### Post by OldDonald on 2011-12-13
Hello!

I have a small problem with the ubuntu 10.04. When I run:

sudo apt-get update

I receive the following:
 
```

Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libjarjar-java-doc (NewFileVer1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

```

What I should do?

Thanks

---

### Post by TeoBigusGeekus on 2011-12-13
Try with this command
```
sudo rm /var/lib/apt/lists/*
```

---

### Post by OldDonald on 2011-12-13
> **TeoBigusGeekus said:**
> Try with this command
```
sudo rm /var/lib/apt/lists/*
```

I get this:

```
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Get:2 http://hu.archive.ubuntu.com hardy Release.gpg [189B]                    
Get:3 http://ppa.launchpad.net intrepid Release.gpg [307B]                     
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ intrepid/main Translation-en_US
Get:4 http://ppa.launchpad.net jaunty Release.gpg [307B]                       
Get:5 http://download.tuxfamily.org lucid Release.gpg [198B]                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Get:6 http://archive.ubuntu.com lucid-updates Release.gpg [198B]               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com lucid-security Release.gpg [198B]              
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ jaunty/main Translation-en_US
Get:8 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Get:9 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ lucid/main Translation-en_US
Ign http://hu.archive.ubuntu.com/ubuntu/ hardy/universe Translation-en_US      
Get:10 http://hu.archive.ubuntu.com hardy-updates Release.gpg [198B]           
Ign http://hu.archive.ubuntu.com/ubuntu/ hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:11 http://ppa.launchpad.net intrepid Release [46.7kB]                      
Ign http://download.tuxfamily.org/glxdock/repository/ubuntu/ lucid/cairo-dock Translation-en_US
Get:12 http://hu.archive.ubuntu.com hardy Release [65.9kB]                     
Get:13 http://archive.ubuntu.com hardy Release.gpg [189B]                      
Ign http://archive.ubuntu.com/ubuntu/ hardy/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ hardy/restricted Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ hardy/universe Translation-en_US         
Get:14 http://download.tuxfamily.org lucid Release [4,215B]                    
Get:15 http://archive.ubuntu.com lucid Release [57.2kB]                        
Get:16 http://ppa.launchpad.net jaunty Release [74.7kB]                        
Get:17 http://download.tuxfamily.org lucid/cairo-dock Packages [4,495B]        
Get:18 http://hu.archive.ubuntu.com hardy-updates Release [58.5kB]             
Get:19 http://archive.ubuntu.com lucid-updates Release [44.7kB]                
Get:20 http://ppa.launchpad.net lucid Release [14.0kB]                         
Get:21 http://archive.ubuntu.com lucid-security Release [44.7kB]               
Get:22 http://ppa.launchpad.net lucid Release [13.9kB]                         
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Sources                             
Get:23 http://hu.archive.ubuntu.com hardy/universe Packages [4,293kB]          
Get:24 http://archive.ubuntu.com hardy Release [65.9kB]                        
Get:25 http://ppa.launchpad.net jaunty/main Packages [1,966B]                  
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Sources                             
Get:26 http://ppa.launchpad.net lucid/main Packages [31.3kB]                   
Get:27 http://archive.ubuntu.com lucid/main Packages [1,386kB]                 
Get:28 http://ppa.launchpad.net lucid/main Packages [41.1kB]                   
Get:29 http://ppa.launchpad.net intrepid/main Packages [1,577B]                
Get:30 http://ppa.launchpad.net intrepid/main Sources [440B]                   
Get:31 http://linux.dropbox.com lucid Release.gpg [489B]                       
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Get:32 http://linux.dropbox.com lucid Release [2,599B]                         
Get:33 http://linux.dropbox.com lucid/main Packages [782B]                     
Get:34 http://archive.ubuntu.com lucid/restricted Packages [6,208B]            
Get:35 http://archive.ubuntu.com lucid/main Sources [659kB]           
Get:36 http://hu.archive.ubuntu.com hardy/universe Sources [1,323kB]           
Get:37 http://hu.archive.ubuntu.com hardy-updates/universe Packages [266kB]    
Get:38 http://archive.ubuntu.com lucid/restricted Sources [3,775B]             
Get:39 http://archive.ubuntu.com lucid/universe Packages [5,448kB]             
Get:40 http://hu.archive.ubuntu.com hardy-updates/universe Sources [65.5kB]    
Get:41 http://archive.ubuntu.com lucid/universe Sources [3,165kB]              
Get:42 http://archive.ubuntu.com lucid/multiverse Packages [180kB]
Get:43 http://archive.ubuntu.com lucid/multiverse Sources [119kB]
Get:44 http://archive.ubuntu.com lucid-updates/main Packages [530kB]
Get:45 http://archive.ubuntu.com lucid-updates/restricted Packages [3,998B]
Get:46 http://archive.ubuntu.com lucid-updates/main Sources [207kB]
Get:47 http://archive.ubuntu.com lucid-updates/restricted Sources [1,850B]
Get:48 http://archive.ubuntu.com lucid-updates/universe Packages [242kB]
Get:49 http://archive.ubuntu.com lucid-updates/universe Sources [84.0kB]
Get:50 http://archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]
Get:51 http://archive.ubuntu.com lucid-updates/multiverse Sources [5,073B]
Get:52 http://archive.ubuntu.com lucid-security/main Packages [239kB]
Get:53 http://archive.ubuntu.com lucid-security/restricted Packages [14B]
Get:54 http://archive.ubuntu.com lucid-security/main Sources [71.8kB]
Get:55 http://archive.ubuntu.com lucid-security/restricted Sources [14B]
Get:56 http://archive.ubuntu.com lucid-security/universe Packages [104kB]
Get:57 http://archive.ubuntu.com lucid-security/universe Sources [27.6kB]
Get:58 http://archive.ubuntu.com lucid-security/multiverse Packages [4,557B]
Get:59 http://archive.ubuntu.com lucid-security/multiverse Sources [1,750B]
Get:60 http://archive.ubuntu.com hardy/main Packages [1,178kB]
Get:61 http://archive.ubuntu.com hardy/restricted Packages [6,986B]
Get:62 http://archive.ubuntu.com hardy/universe Packages [4,293kB]
Get:63 http://archive.ubuntu.com hardy/main Sources [338kB]                    
Get:64 http://archive.ubuntu.com hardy/restricted Sources [1,488B]             
Get:65 http://archive.ubuntu.com hardy/universe Sources [1,323kB]              
Fetched 26.2MB in 9s (2,897kB/s)                                               
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libjarjar-java-doc (NewFileVer1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.


```

---

### Post by TeoBigusGeekus on 2011-12-13
Ok... Rename the folder
```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists_faulty
```
and create a new one
```
sudo mkdir /var/lib/apt/lists/
```

---

### Post by OldDonald on 2011-12-13
now I get:

```

E: Lists directory /var/lib/apt/lists/partial is missing.


```

---

### Post by TeoBigusGeekus on 2011-12-13
> **OldDonald said:**
> now I get:

```

E: Lists directory /var/lib/apt/lists/partial is missing.


```

It shouldn't do this. Read [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=525783").

Anyway, restore the old folder
```
sudo rm -r /var/lib/apt/lists
sudo cp /var/lib/apt/lists_faulty /var/lib/apt/lists
```
keeping a copy just in case and try deleting from the folder again with
```
sudo rm -f /var/lib/apt/lists/*
```

---

### Post by OldDonald on 2011-12-13
sudo rm -f /var/lib/apt/lists/*

```

rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

```

---

### Post by TeoBigusGeekus on 2011-12-13
Do a 
```
sudo apt-get update
```
now.

---

### Post by OldDonald on 2011-12-13
I think that I got the same thing:

```

Hit http://ppa.launchpad.net intrepid Release.gpg
Hit http://archive.ubuntu.com lucid Release.gpg                                                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                                                   
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ intrepid/main Translation-en_US                                                   
Hit http://ppa.launchpad.net jaunty Release.gpg                                                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                                                    
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ jaunty/main Translation-en_US                                                      
Hit http://archive.ubuntu.com lucid-updates Release.gpg                                                                                     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                 
Get:1 http://download.tuxfamily.org lucid Release.gpg [198B]                                                     
Ign http://download.tuxfamily.org/glxdock/repository/ubuntu/ lucid/cairo-dock Translation-en_US                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ lucid/main Translation-en_US                           
Hit http://ppa.launchpad.net intrepid Release                                                                    
Get:2 http://hu.archive.ubuntu.com hardy Release.gpg [189B]                                                      
Ign http://hu.archive.ubuntu.com/ubuntu/ hardy/universe Translation-en_US                                        
Get:3 http://hu.archive.ubuntu.com hardy-updates Release.gpg [198B]                                              
Ign http://hu.archive.ubuntu.com/ubuntu/ hardy-updates/universe Translation-en_US                                
Hit http://linux.dropbox.com lucid Release.gpg                                                                   
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US                                                
Hit http://archive.ubuntu.com lucid-security Release.gpg                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                  
Hit http://ppa.launchpad.net jaunty Release                                                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                
Hit http://archive.ubuntu.com hardy Release.gpg                                                                                        
Get:4 http://hu.archive.ubuntu.com hardy Release [65.9kB]                                                        
Get:5 http://download.tuxfamily.org lucid Release [4,215B]                                                             
Ign http://archive.ubuntu.com/ubuntu/ hardy/main Translation-en_US                                                              
Ign http://archive.ubuntu.com/ubuntu/ hardy/restricted Translation-en_US                                                        
Ign http://archive.ubuntu.com/ubuntu/ hardy/universe Translation-en_US                                    
Hit http://archive.ubuntu.com lucid Release                                                               
Hit http://archive.ubuntu.com lucid-updates Release                                                       
Hit http://archive.ubuntu.com lucid-security Release                                                      
Hit http://ppa.launchpad.net lucid Release                                                                                                            
Hit http://ppa.launchpad.net lucid Release                                                                                                            
Hit http://archive.ubuntu.com hardy Release                                                                                                            
Ign http://ppa.launchpad.net intrepid/main Packages                                                                      
Ign http://ppa.launchpad.net intrepid/main Sources                                                                       
Hit http://archive.ubuntu.com lucid/main Packages                                                                        
Hit http://archive.ubuntu.com lucid/restricted Packages                                                                  
Hit http://archive.ubuntu.com lucid/main Sources                                                   
Hit http://archive.ubuntu.com lucid/restricted Sources                                             
Hit http://archive.ubuntu.com lucid/universe Packages                                              
Hit http://archive.ubuntu.com lucid/universe Sources                                                                     
Hit http://ppa.launchpad.net jaunty/main Packages                                                                        
Hit http://archive.ubuntu.com lucid/multiverse Packages                                            
Hit http://archive.ubuntu.com lucid/multiverse Sources                                             
Hit http://archive.ubuntu.com lucid-updates/main Packages                                          
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                                    
Hit http://archive.ubuntu.com lucid-updates/main Sources                                                                 
Hit http://archive.ubuntu.com lucid-updates/restricted Sources                                                           
Hit http://archive.ubuntu.com lucid-updates/universe Packages                                                            
Get:6 http://download.tuxfamily.org lucid/cairo-dock Packages [4,495B]                                                   
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Ign http://ppa.launchpad.net intrepid/main Packages                                                
Hit http://ppa.launchpad.net lucid/main Packages                                                   
Hit http://archive.ubuntu.com lucid-updates/universe Sources                                                             
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                                    
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources               
Get:7 http://hu.archive.ubuntu.com hardy-updates Release [58.5kB]            
Hit http://archive.ubuntu.com lucid-security/main Packages                                                                 
Hit http://archive.ubuntu.com lucid-security/restricted Packages                                                           
Hit http://archive.ubuntu.com lucid-security/main Sources                                            
Hit http://archive.ubuntu.com lucid-security/restricted Sources                                      
Hit http://archive.ubuntu.com lucid-security/universe Packages                                       
Ign http://ppa.launchpad.net intrepid/main Sources                                                   
Hit http://archive.ubuntu.com lucid-security/universe Sources                                                              
Hit http://archive.ubuntu.com lucid-security/multiverse Packages                                   
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                                    
Hit http://archive.ubuntu.com hardy/main Packages                                                  
Hit http://archive.ubuntu.com hardy/restricted Packages                                            
Hit http://archive.ubuntu.com hardy/universe Packages                                              
Hit http://archive.ubuntu.com hardy/main Sources                                                   
Hit http://ppa.launchpad.net intrepid/main Packages                                                
Hit http://archive.ubuntu.com hardy/restricted Sources                                       
Hit http://archive.ubuntu.com hardy/universe Sources                                                               
Hit http://ppa.launchpad.net intrepid/main Sources                                                                 
Get:8 http://hu.archive.ubuntu.com hardy/universe Packages [4,293kB] 
Hit http://linux.dropbox.com lucid Release             
Hit http://linux.dropbox.com lucid/main Packages       
Get:9 http://hu.archive.ubuntu.com hardy/universe Sources [1,323kB]
Get:10 http://hu.archive.ubuntu.com hardy-updates/universe Packages [266kB]
Get:11 http://hu.archive.ubuntu.com hardy-updates/universe Sources [65.5kB]
Fetched 6,081kB in 6s (963kB/s)                                                                                                                             
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libjarjar-java-doc (NewFileVer1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.


```

I am new in ubuntu :S

---

