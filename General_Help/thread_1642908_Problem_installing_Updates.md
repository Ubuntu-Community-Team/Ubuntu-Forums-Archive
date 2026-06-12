---
title: "Problem installing Updates"
date: 2010-12-11
forum: General Help
---

### Post by imranmcse on 2010-12-11
I am using Ubuntu 10.10. When I check updates it shows me there are some updates available for gwibber client. "wibber-service-facebook gwibber-service-identica gwibber-service-twitter" 
But when I try to install it shows me error message "Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

How can I solve this issue?

---

### Post by Jahid65 on 2010-12-11
It's probably not a big problem. you can install that.

---

### Post by imranmcse on 2010-12-11
> **Jahid65 said:**
> It's probably not a big problem. you can install that.

But its not. I can't continue the installation.

---

### Post by sikander3786 on 2010-12-11
> **imranmcse said:**
> But its not. I can't continue the installation.
Please post the output of this command.

Applications > Accessories > Terminal:
```
sudo apt-get update
```

While posting, click the # icon and paste your text in between the generated code tags.

---

### Post by imranmcse on 2010-12-11
> **Jahid65 said:**
> It's probably not a big problem. you can install that.

> **sikander3786 said:**
> Please post the output of this command.

Applications > Accessories > Terminal:
```
sudo apt-get update
```

While posting, click the # icon and paste your text in between the generated code tags.

```
Ign http://download.skype.com stable Release.gpg                               
Hit http://extras.ubuntu.com maverick Release.gpg                              
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://ubuntuarchive.hnsdc.com maverick Release.gpg                        
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-en
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-en_US
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en        
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_US
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en_US     
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://download.skype.com stable Release                                   
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex          
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en  
Hit http://linux.dropbox.com maverick Release                                  
Hit http://download.skype.com stable/non-free i386 Packages                    
Hit http://linux.dropbox.com maverick/main i386 Packages             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_US
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en_US
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release.gpg
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en_US
Get:6 http://ppa.launchpad.net maverick Release [57.3kB]
Ign http://ppa.launchpad.net maverick Release                          
Get:7 http://ppa.launchpad.net maverick Release [9,752B]               
Ign http://ppa.launchpad.net maverick Release                          
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en
Get:8 http://ppa.launchpad.net maverick Release [39.8kB]
Ign http://ppa.launchpad.net maverick Release          
Hit http://ppa.launchpad.net maverick Release    
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en_US
Get:9 http://ppa.launchpad.net maverick Release [39.8kB]                   
Ign http://ppa.launchpad.net maverick Release                          
Get:10 http://ppa.launchpad.net maverick Release [57.3kB]              
Ign http://ppa.launchpad.net maverick Release           
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://ppa.launchpad.net maverick Release  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://ubuntuarchive.hnsdc.com maverick-security Release.gpg               
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ubuntuarchive.hnsdc.com maverick Release                            
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release                    
Hit http://ubuntuarchive.hnsdc.com maverick-security Release                   
Hit http://ubuntuarchive.hnsdc.com maverick/main Sources                       
Hit http://ubuntuarchive.hnsdc.com maverick/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/main Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse i386 Packages
Fetched 1,585B in 24s (66B/s)
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5AFADBD4AA1C92B0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 35DA01C261E46227
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by karthick87 on 2010-12-11
You can get rid of the 404 error by unticking the PPA in Software Sources..Also Run the following commands in terminal,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
``````

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA1C92B0
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E46227

``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220

``````
sudo apt-get update
```

---

### Post by imranmcse on 2010-12-11
> **karthick87 said:**
> You can get rid of the 404 error by unticking the PPA in Software Sources..Also Run the following commands in terminal,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
``````

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AA1C92B0
``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E46227

``````
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220

``````
sudo apt-get update
```

Thanks for your help, but now once I run sudo apt-get update I got following output with some errors. 
```
sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-en
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Hit http://ubuntuarchive.hnsdc.com maverick Release.gpg          
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US
Hit http://linux.dropbox.com maverick Release  
Hit http://linux.dropbox.com maverick/main i386 Packages             
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en    
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en_US
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release.gpg
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en
Hit http://ppa.launchpad.net maverick Release                              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://ppa.launchpad.net maverick Release  
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick Release                              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://ppa.launchpad.net maverick Release                              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net maverick Release                              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://ubuntuarchive.hnsdc.com maverick-security Release.gpg           
Ign http://ppa.launchpad.net maverick Release
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main i386 Packages                   
Hit http://ppa.launchpad.net maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main i386 Packages                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                   
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources   
Hit http://ppa.launchpad.net maverick/main i386 Packages                   
Hit http://ppa.launchpad.net maverick/main Sources                         
Hit http://ppa.launchpad.net maverick/main i386 Packages                   
Ign http://ppa.launchpad.net maverick/main Sources                         
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en_US
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ubuntuarchive.hnsdc.com maverick Release
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release                    
Hit http://ubuntuarchive.hnsdc.com maverick-security Release                   
Hit http://ubuntuarchive.hnsdc.com maverick/main Sources                       
Hit http://ubuntuarchive.hnsdc.com maverick/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/main Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe Sources
Hit http://ubuntuarchive.hnsdc.com maverick-security/main i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe i386 Packages
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse i386 Packages
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by karthick87 on 2010-12-11
Goto System>>Administration>>Software Sources>>Other Sotware and uncheck that PPA and run the update again..

```
sudo apt-get update
```

---

### Post by imranmcse on 2010-12-11
> **karthick87 said:**
> Goto System>>Administration>>Software Sources>>Other Sotware and uncheck that PPA and run the update again..

```
sudo apt-get update
```

There are so many PPA entries, which one shall I remove?

---

### Post by karthick87 on 2010-12-11
Can you post the output of,

```
cat /etc/apt/sources.list
```

---

### Post by imranmcse on 2010-12-11
> **karthick87 said:**
> Can you post the output of,

```
cat /etc/apt/sources.list
```

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://ubuntuarchive.hnsdc.com/ubuntu/ maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick main restricted
deb-src http://ubuntuarchive.hnsdc.com/ubuntu/ maverick multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates main restricted
deb-src http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick universe
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick multiverse
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security main restricted
deb-src http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security restricted main multiverse universe #Added by software-properties
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security universe
deb http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security multiverse
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main

```

---

### Post by karthick87 on 2010-12-11
Uncomment these two lines,by putiing # sign in-front

```
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
```

and then run update,

```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-12-11
@karthick87:

I am not sure if the PPAs you mentioned above are causing a problem here. Lets see what the OP comes up with.

@OP:

If that doesn't solve the problem, please post the output of this command.

```
ls /etc/apt/sources.list.d
```

---

### Post by imranmcse on 2010-12-11
> **karthick87 said:**
> Uncomment these two lines,by putiing # sign in-front

```
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
```

and then run update,

```
sudo apt-get update
```

No success :(
Output is below:
```
sudo apt-get update
Hit http://archive.canonical.com maverick Release.gpg
Hit http://ubuntuarchive.hnsdc.com maverick Release.gpg                        
Hit http://extras.ubuntu.com maverick Release.gpg                              
Hit http://linux.dropbox.com maverick Release.gpg                              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en        
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/main Translation-en_US     
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en  
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                        
Hit http://linux.dropbox.com maverick/main i386 Packages             
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick/universe Translation-en_US
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release.gpg
Ign http://ppa.launchpad.net/sevenmachines/flash/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ppa.launchpad.net maverick Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ maverick/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en
Get:7 http://ppa.launchpad.net maverick Release [9,752B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:8 http://ppa.launchpad.net maverick Release [39.8kB]               
Hit http://ubuntuarchive.hnsdc.com maverick-security Release.gpg
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en
Get:9 http://ppa.launchpad.net maverick Release [57.3kB]               
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en
Get:10 http://ppa.launchpad.net maverick Release [39.8kB]              
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en
Get:11 http://ppa.launchpad.net maverick Release [57.3kB]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/restricted Translation-en_US
Get:12 http://ppa.launchpad.net maverick Release [9,753B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en
Ign http://ppa.launchpad.net maverick Release  
Get:13 http://ppa.launchpad.net maverick/main Sources [792B]
Ign http://ubuntuarchive.hnsdc.com/ubuntu/ maverick-security/universe Translation-en_US
Get:14 http://ppa.launchpad.net maverick/main i386 Packages [2,194B]
Hit http://ubuntuarchive.hnsdc.com maverick Release                   
Get:15 http://ppa.launchpad.net maverick/main Sources [683B]                   
Get:16 http://ppa.launchpad.net maverick/main i386 Packages [1,105B]           
Hit http://ubuntuarchive.hnsdc.com maverick-updates Release           
Get:17 http://ppa.launchpad.net maverick/main i386 Packages [699B]             
Hit http://ubuntuarchive.hnsdc.com maverick-security Release                   
Get:18 http://ppa.launchpad.net maverick/main i386 Packages [14B]              
Get:19 http://ppa.launchpad.net maverick/main Sources [522B]                   
Hit http://ubuntuarchive.hnsdc.com maverick/main Sources                       
Hit http://ubuntuarchive.hnsdc.com maverick/restricted Sources                 
Get:20 http://ppa.launchpad.net maverick/main i386 Packages [591B]             
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse Sources                 
Get:21 http://ppa.launchpad.net maverick/main Sources [2,502B]                 
Get:22 http://ppa.launchpad.net maverick/main i386 Packages [3,579B]           
Hit http://ubuntuarchive.hnsdc.com maverick/universe Sources                   
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://ubuntuarchive.hnsdc.com maverick/main i386 Packages                 
Hit http://ubuntuarchive.hnsdc.com maverick/restricted i386 Packages           
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://ubuntuarchive.hnsdc.com maverick/universe i386 Packages             
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ubuntuarchive.hnsdc.com maverick/multiverse i386 Packages           
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted Sources         
Err http://ppa.launchpad.net maverick/main Sources                             
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages                       
  404  Not Found
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main Sources               
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse Sources         
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe Sources           
Hit http://ubuntuarchive.hnsdc.com maverick-updates/main i386 Packages         
Hit http://ubuntuarchive.hnsdc.com maverick-updates/restricted i386 Packages   
Hit http://ubuntuarchive.hnsdc.com maverick-updates/universe i386 Packages     
Hit http://ubuntuarchive.hnsdc.com maverick-updates/multiverse i386 Packages   
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted Sources        
Hit http://ubuntuarchive.hnsdc.com maverick-security/main Sources              
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse Sources        
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe Sources          
Hit http://ubuntuarchive.hnsdc.com maverick-security/main i386 Packages        
Hit http://ubuntuarchive.hnsdc.com maverick-security/restricted i386 Packages  
Hit http://ubuntuarchive.hnsdc.com maverick-security/universe i386 Packages    
Hit http://ubuntuarchive.hnsdc.com maverick-security/multiverse i386 Packages  
Fetched 228kB in 9s (24.0kB/s)                                                 
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by karthick87 on 2010-12-11
By [sikander3786]("http://ubuntuforums.org/member.php?u=806649") suggestion post the output of,

```
ls /etc/apt/sources.list.d
```

---

### Post by imranmcse on 2010-12-11
> **karthick87 said:**
> By [sikander3786]("http://ubuntuforums.org/member.php?u=806649") suggestion post the output of,

```
ls /etc/apt/sources.list.d
```

```
ls /etc/apt/sources.list.d
dropbox.list                          sevenmachines-flash.list
dropbox.list.save                     sevenmachines-flash.list.save
gwibber-daily-ppa-maverick.list       skype.list
gwibber-daily-ppa-maverick.list.save  tualatrix-ppa-maverick.list
gwibber-team-ppa-maverick.list        tualatrix-ppa-maverick.list.save
gwibber-team-ppa-maverick.list.save   ubuntu-wine-ppa-maverick.list
maverick-partner.list                 ubuntu-wine-ppa-maverick.list.save
maverick-partner.list.save            user-ppa-name-maverick.list
pdfmod-team-ppa.list                  user-ppa-name-maverick.list.save

```

---

### Post by sikander3786 on 2010-12-11
Software Center > Edit > Software Sources > Other Software Tab and uncheck these 2.

```
user-ppa-name-maverick.list
user-ppa-name-maverick.list.save
```

And you might want to enable the 2 in sources.list that your commented previously in order to install software from those sources.

```
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu maverick main
```

Hope there are no more errors :-)

---

### Post by imranmcse on 2010-12-11
Thanks Buddy for your help. Now there are no more errors.

---

### Post by karthick87 on 2010-12-11
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

