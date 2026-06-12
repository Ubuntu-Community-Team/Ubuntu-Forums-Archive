---
title: "&quot;E: Some index files failed to download, they have been ignored&quot;"
date: 2010-12-27
forum: General Help
---

### Post by TheNerdAL on 2010-12-27
When I update in terminal it gives me this: 

```
adrian@adrian-desktop:~$ sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                                  
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://apt.boxee.tv maverick Release.gpg                                   
Ign http://apt.boxee.tv/ maverick/main Translation-en                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Get:2 http://download.tuxfamily.org  Release.gpg [198B]                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Get:3 http://dl.google.com stable Release.gpg [197B]                           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/ maverick/main Translation-en
Ign http://apt.boxee.tv/ maverick/main Translation-en_US                       
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en         
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en_US      
Ign http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://apt.boxee.tv maverick Release                                       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://apt.boxee.tv maverick/main i386 Packages/DiffIndex                  
Get:4 http://download.tuxfamily.org  Release [724B]                            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://apt.boxee.tv maverick/main i386 Packages                            
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-proposed Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en    
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US 
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://download.tuxfamily.org  Packages                                    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Get:5 http://dl.google.com stable Release [1,347B]                             
Ign http://download.tuxfamily.org  Packages                                    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-backports Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en   
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Get:6 http://download.tuxfamily.org  Packages [7,260B]                         
Get:7 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://archive.ubuntu.com maverick Release                       
Hit http://archive.ubuntu.com maverick-updates Release               
Hit http://archive.ubuntu.com maverick-proposed Release              
Hit http://archive.ubuntu.com maverick-backports Release             
Get:8 http://dl.google.com stable/main i386 Packages [1,076B]                  
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://archive.ubuntu.com maverick/universe Sources              
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Get:9 http://dl.google.com stable/main i386 Packages [735B]
Hit http://archive.ubuntu.com maverick/main Sources                    
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-proposed/universe Sources
Hit http://archive.ubuntu.com maverick-proposed/main Sources
Hit http://archive.ubuntu.com maverick-proposed/multiverse Sources
Hit http://archive.ubuntu.com maverick-proposed/restricted Sources
Hit http://archive.ubuntu.com maverick-proposed/universe i386 Packages
Hit http://archive.ubuntu.com maverick-proposed/main i386 Packages
Hit http://archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-proposed/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-backports/universe Sources
Hit http://archive.ubuntu.com maverick-backports/main Sources
Hit http://archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://archive.ubuntu.com maverick-backports/restricted Sources
Hit http://archive.ubuntu.com maverick-backports/universe i386 Packages
Hit http://archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://archive.ubuntu.com maverick-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-backports/restricted i386 Packages
Fetched 13.1kB in 2s (6,052B/s)
W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
adrian@adrian-desktop:~$ 

```

At the end it has this error: ```
E: Some index files failed to download, they have been ignored, or old ones used instead.
``` 

How can I fix that? 

And how can I fix the other errors before it? ```
W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
```

Thanks.

---

### Post by wojox on 2010-12-27
Go into Software Sources > Other Software and remove the conflicting ppa's.

---

### Post by susema on 2010-12-27
Look here please;

[http://ubuntuforums.org/showthread.php?p=10278131#post10278131](http://ubuntuforums.org/showthread.php?p=10278131#post10278131)

---

### Post by TheNerdAL on 2010-12-27
> **wojox said:**
> Go into Software Sources > Other Software and remove the conflicting ppa's.

That fixed both issues! Thanks! :)

---

