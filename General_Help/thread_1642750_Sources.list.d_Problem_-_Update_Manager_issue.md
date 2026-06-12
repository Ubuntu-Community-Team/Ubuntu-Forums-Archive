---
title: "Sources.list.d Problem - Update Manager issue"
date: 2010-12-10
forum: General Help
---

### Post by angus_young on 2010-12-10
Hi Everyone,

I am Having similar problems to the OP in this solved thread

when I run Update Manager I get the following error

```
Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.
```

[http://ubuntuforums.org/showthread.php?t=1642254&page=2](http://ubuntuforums.org/showthread.php?t=1642254&page=2)

Can anyone help, here is my output from sudo apt-get update

```
Err http://archive.canonical.com maverick Release.gpg                          
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
  Unable to connect to 68.199.83.207:7212:
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
  Unable to connect to 68.199.83.207:7212:
Err http://dl.google.com stable Release.gpg                                    
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
  Unable to connect to 68.199.83.207:7212:
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB       
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick Release.gpg                          
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
  Unable to connect to 68.199.83.207:7212:
Err http://extras.ubuntu.com maverick Release.gpg                              
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
  Unable to connect to 68.199.83.207:7212:
Err http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-updates Release.gpg                  
  Unable to connect to 68.199.83.207:7212:
Ign http://archive.canonical.com maverick Release                              
Err http://linux.dropbox.com maverick Release.gpg                              
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
  Unable to connect to 68.199.83.207:7212:
Err http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_GB           
  Unable to connect to 68.199.83.207:7212:
Ign http://dl.google.com stable Release                                        
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-security Release.gpg
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
  Unable to connect to 68.199.83.207:7212:
Ign http://extras.ubuntu.com maverick Release   
Ign http://archive.canonical.com maverick/partner Sources
Ign http://linux.dropbox.com maverick Release   
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com maverick/main Sources/DiffIndex
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Unable to connect to 68.199.83.207:7212:
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex      
Ign http://linux.dropbox.com maverick/main i386 Packages/DiffIndex             
Ign http://dl.google.com stable/main i386 Packages                             
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-proposed Release.gpg
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Ign http://extras.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://archive.canonical.com maverick/partner Sources
Ign http://linux.dropbox.com maverick/main i386 Packages
Ign http://dl.google.com stable/main i386 Packages
Ign http://extras.ubuntu.com maverick/main Sources
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Ign http://gb.archive.ubuntu.com maverick Release
Ign http://gb.archive.ubuntu.com maverick-updates Release
Ign http://gb.archive.ubuntu.com maverick-security Release
Ign http://gb.archive.ubuntu.com maverick-proposed Release
Ign http://archive.canonical.com maverick/partner i386 Packages
Ign http://linux.dropbox.com maverick/main i386 Packages
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex
Ign http://gb.archive.ubuntu.com maverick-security/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/restricted i386 Packages
Err http://archive.canonical.com maverick/partner Sources
  Unable to connect to 68.199.83.207:7212:
Err http://linux.dropbox.com maverick/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://ppa.launchpad.net maverick Release.gpg
  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)
Err http://ppa.launchpad.net/voria/ppa/ubuntu/ maverick/main Translation-en
  Unable to connect to 68.199.83.207:7212:
Err http://ppa.launchpad.net/voria/ppa/ubuntu/ maverick/main Translation-en_GB
  Unable to connect to 68.199.83.207:7212:
Ign http://extras.ubuntu.com maverick/main Sources
Ign http://gb.archive.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Ign http://archive.canonical.com maverick/partner i386 Packages
Ign http://ppa.launchpad.net maverick Release
Ign http://extras.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-security/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/main i386 Packages
Err http://archive.canonical.com maverick/partner i386 Packages
  Unable to connect to 68.199.83.207:7212:
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex
Err http://extras.ubuntu.com maverick/main Sources
  Unable to connect to 68.199.83.207:7212:
Ign http://gb.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-proposed/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick/universe i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Ign http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex
Err http://extras.ubuntu.com maverick/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-security/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-security/restricted i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-security/multiverse i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-security/universe i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-proposed/restricted i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-proposed/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-proposed/universe i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick/restricted i386 Packages
  Unable to connect to 68.199.83.207:7212:
Ign http://ppa.launchpad.net maverick/main Sources
Err http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick/universe i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  Unable to connect to 68.199.83.207:7212:
Err http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
  Unable to connect to 68.199.83.207:7212:
Ign http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ppa.launchpad.net maverick/main Sources
Ign http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  Unable to connect to 68.199.83.207:7212:
Err http://ppa.launchpad.net maverick/main i386 Packages
  Unable to connect to 68.199.83.207:7212:
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/Release.gpg  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/maverick/Release.gpg  Could not connect to 68.199.83.207:7212 (68.199.83.207). - connect (110: Connection timed out)

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_GB.bz2  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/maverick/main/source/Sources.gz  Unable to connect to 68.199.83.207:7212:

W: Failed to fetch http://ppa.launchpad.net/voria/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Unable to connect to 68.199.83.207:7212:

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Also the output from my cat /etc/apt/sources.list

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

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

deb http://gb.archive.ubuntu.com/ubuntu/ maverick-security main restricted multiverse universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe

```

And Finally the output from /ect/apt$ ls sources.list.d

```
/etc/apt$ ls sources.list.d
dropbox.list       google-chrome.list       voria-ppa-maverick.list
dropbox.list.save  google-chrome.list.save  voria-ppa-maverick.list.save
```

I hope you guys can help, Thanks

A.Y.

---

### Post by tommcd on 2010-12-10
Are you able to access your mirror [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) now? I can access it as of this writing in Firefox.

Also, as I could have guessed, you have a boatload of 3rd party repos in your */etc/apt/sources.list.d/* directory. No doubt one of these repos has gone rogue and is causing the *Requires installation of untrusted packages* error.
Be sure you have added the appropriate GPG key for each of those repos.

Or better yet, follow my method for avoiding all problems with Ubuntu:
1. Always do clean installs, never do dist-upgrades.
2. *Avoid all 3rd party repos. This includes those all too often problematic PPA repos*.

---

### Post by drs305 on 2010-12-10
I agree. I loaded your sources.list file and it ran fine for me. Your server may have been down for a while.

You can deselect the third-party sources via Synaptic or Software Sources (Settings, Repositories, Third Party) and add them back one at a time to see which one(s) produce the authentication message.

Also, if they are ppa's, an easy way to add them to your sources, and include the authentication key automatically, is with the *add-apt-repository* command. You can view the man page to learn more about it:
```

man add-apt-repository
```
Example: sudo add-apt-repository ppa:nhandler

---

### Post by CompyTheInsane on 2010-12-10
From your apt-get update output, it looks as if you were behind a proxy server when running apt-get update.

Are you behind a proxy server by any chance?

If so, it may be likely that apt-get update failed because it was unable to contact the proxy server .

---

### Post by angus_young on 2010-12-11
Thanks everyone

@compugeek32, thanks i was behind a proxy, i thought i just changed it in chrome but i did it system wide

oops,

Thanks again Guys

---

