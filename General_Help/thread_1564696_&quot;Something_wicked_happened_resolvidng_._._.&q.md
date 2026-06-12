---
title: "&quot;Something wicked happened resolvidng . . .&quot;"
date: 2010-08-30
forum: General Help
---

### Post by krapp on 2010-08-30
Hi--I was following the official Ubuntu documentation for installing Opera from the repositories, and after adding the sofware sources, the Opera key, getting the error messages, installing the Opera keyring as the documentation indicates, I got the following after doing apt-get update. My concerns aren't about Opera but the error messages I got in connection with the Ubuntu repositories (they appear at the end):

```
~$ sudo apt-get update
0% [Connecting to us.archive.ubuntu.com] [Connecting to security.ubuntu.com] [C
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US              
Hit http://linux.dropbox.com lucid Release                                     
Hit http://linux.dropbox.com lucid/main Packages                               
Get:1 http://archive.getdeb.net lucid-getdeb Release.gpg [836B]                
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-en_US     
Get:2 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/aheck/ppa/ubuntu/ lucid/main Translation-en_US    
Get:3 http://security.ubuntu.com lucid-security Release.gpg [189B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://deb.opera.com stable Release.gpg [189B]                           
Ign http://deb.opera.com/opera-beta/ stable/non-free Translation-en_US         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/main Packages                    
Get:5 http://deb.opera.com stable Release [1,067B]                             
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://archive.getdeb.net lucid-getdeb Release                             
Err http://us.archive.ubuntu.com lucid Release.gpg                             
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.getdeb.net lucid-getdeb/games Packages                   
Ign http://archive.getdeb.net lucid-getdeb/games Packages                      
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.getdeb.net lucid-getdeb/games Packages                   
  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 2,588B in 55s (47B/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/games/binary-amd64/Packages.gz  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

What's thing "Something wicked happened" all about? should I be worried?

Thanks.

---

### Post by MooPi on 2010-08-30
Thats a new one. Or I've never really looked when the update failure occurred. It may just be the server you were trying to access was down. Try again later to verify.

---

