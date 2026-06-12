---
title: "update trouble."
date: 2010-01-09
forum: General Help
---

### Post by Jackzor on 2010-01-09
I'm not sure if I broke it or what.

Someone help me out though. I can't update my ubuntu 

It doesn't get past preparing to upgrade. and config files you need to see.. Just give me the command to output. Thanks.

---

### Post by spiderbatdad on 2010-01-09
might help if you run ```
sudo apt-get update
``` and paste the output here so we can see what happens. Please use CODE tags...paste the output inside the words CODE when you click the # symbol in menu of this reply editor.

---

### Post by Jackzor on 2010-01-09
```
nicholas@nicholas-laptop:~$ sudo apt-get update
Hit http://archive.ubuntu.com dapper Release.gpg                               
Ign http://archive.ubuntu.com dapper/main Translation-en_US                    
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://archive.ubuntu.com dapper/restricted Translation-en_US              
Ign http://archive.ubuntu.com dapper/universe Translation-en_US                
Ign http://archive.ubuntu.com dapper/multiverse Translation-en_US              
Hit http://archive.ubuntu.com dapper-updates Release.gpg                       
Ign http://archive.ubuntu.com dapper-updates/main Translation-en_US            
Ign http://archive.ubuntu.com dapper-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com dapper-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com dapper-updates/multiverse Translation-en_US      
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com dapper-security Release.gpg                     
Ign http://security.ubuntu.com dapper-security/main Translation-en_US          
Ign http://security.ubuntu.com dapper-security/restricted Translation-en_US    
Ign http://security.ubuntu.com dapper-security/universe Translation-en_US      
Ign http://security.ubuntu.com dapper-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://archive.ubuntu.com dapper-backports Release.gpg                     
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://archive.ubuntu.com dapper-backports/main Translation-en_US          
Hit http://security.ubuntu.com dapper-security Release                         
Ign http://archive.ubuntu.com dapper-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com dapper-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com dapper-backports/multiverse Translation-en_US    
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://archive.ubuntu.com dapper Release                                   
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Get:1 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]           
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.ubuntu.com dapper-updates Release                           
Hit http://archive.ubuntu.com dapper-backports Release                         
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://packages.medibuntu.org karmic Release                               
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://deb.opera.com stable Release                                        
Hit http://archive.canonical.com karmic Release                                
Hit http://archive.ubuntu.com dapper/main Packages                             
Hit http://archive.ubuntu.com dapper/restricted Packages                       
Hit http://archive.ubuntu.com dapper/universe Packages                         
Get:2 http://us.archive.ubuntu.com karmic-updates Release [44.1kB]             
Hit http://archive.ubuntu.com dapper/multiverse Packages                       
Hit http://archive.ubuntu.com dapper/main Sources                              
Hit http://archive.ubuntu.com dapper/restricted Sources                        
Hit http://archive.ubuntu.com dapper/universe Sources                          
Hit http://archive.ubuntu.com dapper/multiverse Sources                        
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://archive.ubuntu.com dapper-updates/main Packages                     
Hit http://archive.ubuntu.com dapper-updates/restricted Packages               
Hit http://archive.ubuntu.com dapper-updates/universe Packages                 
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages               
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://security.ubuntu.com dapper-security/main Packages                   
Hit http://security.ubuntu.com dapper-security/restricted Packages             
Hit http://deb.opera.com stable Release                                        
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://us.archive.ubuntu.com karmic/universe Sources                       
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://archive.ubuntu.com dapper-updates/main Sources                      
Hit http://archive.ubuntu.com dapper-updates/restricted Sources                
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://packages.medibuntu.org karmic/free Sources                          
Hit http://ppa.launchpad.net karmic/main Packages                              
Get:3 http://us.archive.ubuntu.com karmic-updates/main Packages [129kB]        
Hit http://packages.medibuntu.org karmic/non-free Sources                      
Hit http://security.ubuntu.com dapper-security/universe Packages               
Hit http://security.ubuntu.com dapper-security/multiverse Packages             
Hit http://security.ubuntu.com dapper-security/main Sources                    
Hit http://security.ubuntu.com dapper-security/restricted Sources              
Hit http://security.ubuntu.com dapper-security/universe Sources                
Hit http://security.ubuntu.com dapper-security/multiverse Sources              
Hit http://archive.ubuntu.com dapper-updates/universe Sources                  
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources                
Hit http://archive.ubuntu.com dapper-backports/main Packages                   
Hit http://archive.ubuntu.com dapper-backports/restricted Packages             
Hit http://archive.ubuntu.com dapper-backports/universe Packages               
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages             
Hit http://archive.ubuntu.com dapper-backports/main Sources                    
Hit http://archive.ubuntu.com dapper-backports/restricted Sources              
Hit http://archive.ubuntu.com dapper-backports/universe Sources                
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources              
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Ign http://deb.opera.com stable/non-free Packages                              
Get:4 http://us.archive.ubuntu.com karmic-updates/restricted Packages [14B]    
Get:5 http://us.archive.ubuntu.com karmic-updates/main Sources [39.7kB]        
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://deb.opera.com stable/non-free Packages                              
Get:6 http://us.archive.ubuntu.com karmic-updates/restricted Sources [14B]     
Get:7 http://us.archive.ubuntu.com karmic-updates/universe Packages [78.6kB]   
Get:8 http://us.archive.ubuntu.com karmic-updates/universe Sources [19.1kB]    
Get:9 http://us.archive.ubuntu.com karmic-updates/multiverse Packages [6,942B] 
Get:10 http://us.archive.ubuntu.com karmic-updates/multiverse Sources [3,831B] 
Err http://packages.freecontrib.org dapper Release.gpg                         
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err http://packages.freecontrib.org dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Err http://packages.freecontrib.org dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org http:
Fetched 322kB in 2min 0s (2,661B/s)                       
Reading package lists... Done
W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
nicholas@nicholas-laptop:~$ 

```

---

### Post by Jackzor on 2010-01-09
bump

---

### Post by Jackzor on 2010-01-09
...Please help? I'd like to get my updates.

---

### Post by Jackzor on 2010-01-09
?

---

### Post by n8ek on 2010-01-09
I have the same problem i think?, my Ubuntu 9.10 just will not update it just seems to hang when updateing

---

### Post by Jackzor on 2010-01-09
> **n8ek said:**
> I have the same problem i think?, my Ubuntu 9.10 just will not update it just seems to hang when updateing

Lol. Well. Surly someone that has a bit more knowing than us has fixed it. Just gotta have that person see this post. I can't stand it.

---

### Post by l-x-l on 2010-01-09
I'm no expert but it looks like you're mixing repos. (Which I thought was a big no-no). What version of Ubuntu are you running Dapper Drake or Karmic? Because I see both in your post.

---

### Post by Jackzor on 2010-01-09
Its 9.10 Lol. I did do something with the sources list.. But it was a few days ago and I can't even remember what I did. I have been thinking thats what it was.

---

### Post by Jackzor on 2010-01-09
Sorry, I figured it all out. Thanks to your imput.

---

