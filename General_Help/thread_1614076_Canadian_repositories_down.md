---
title: "Canadian repositories down?"
date: 2010-11-05
forum: General Help
---

### Post by kirk.mactavish on 2010-11-05
Below is my sudo apt-get update output (Ubuntu 10.10).

1. Any idea why there are so many ignores?

2. Any ideas on fixing these errors: 

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

Thanks!

```
sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://linux.dropbox.com maverick Release                                  
Hit http://linux.dropbox.com maverick/main amd64 Packages                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA           
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://extras.ubuntu.com maverick/main amd64 Packages                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://security.ubuntu.com maverick-security/restricted Sources    
Hit http://security.ubuntu.com maverick-security/universe Sources      
Hit http://security.ubuntu.com maverick-security/multiverse Sources    
Hit http://security.ubuntu.com maverick-security/main amd64 Packages           
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages     
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages       
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages     
Err http://ca.archive.ubuntu.com maverick Release.gpg                          
  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                            
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Get:1 http://dl.google.com stable Release [1,338B]
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex
Hit http://ca.archive.ubuntu.com maverick-updates Release
Get:2 http://dl.google.com stable/main amd64 Packages [630B]
Ign http://ca.archive.ubuntu.com maverick/main Sources/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/restricted Sources/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/universe Sources/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/multiverse Sources/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/main amd64 Packages/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/restricted amd64 Packages/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/universe amd64 Packages/DiffIndex
Ign http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages/DiffIndex
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/main Sources
Hit http://ca.archive.ubuntu.com maverick/restricted Sources
Hit http://ca.archive.ubuntu.com maverick/universe Sources
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages
Fetched 1,968B in 11s (173B/s)
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'ca.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by searchfgold6789 on 2010-11-05
if sudo apt-get update worked before and just stopped working all of a sudden, maybe the repositories for Canada are down, which would surprise me.
Opening the files in my browser works fine.

EDIT: Opening the files in my browser does not work fine! I get a 404.

---

