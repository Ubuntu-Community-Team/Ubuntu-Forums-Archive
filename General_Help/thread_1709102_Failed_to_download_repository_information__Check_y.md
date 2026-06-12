---
title: "Failed to download repository information  Check your Internet connection."
date: 2011-03-17
forum: General Help
---

### Post by MotherMonster on 2011-03-17
Whenever I go to update I press check and I get

"Failed to download repository information

Check your Internet connection."

Well obviously I don't need to check my internet connection if I'm posting this thread. I am using Google Chrome and it's as fast as can be. When I run ```
sudo apt-get update
``` I get the following:

```
Get:1 http://dl.google.com stable Release.gpg [197B]
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://download.skype.com stable Release.gpg                               
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com maverick Release                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en
Ign http://download.skype.com/linux/repos/debian/ stable/non-free Translation-en_US
Get:2 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en    
Hit http://archive.canonical.com maverick/partner i386 Packages                
Get:3 http://dl.google.com stable/main i386 Packages [1,075B]                  
Ign http://download.skype.com stable Release                                   
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Ign http://download.skype.com stable/non-free Sources                
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release 
Hit http://archive.ubuntu.com maverick-updates Release               
Hit http://archive.ubuntu.com maverick-security Release              
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex
Hit http://archive.ubuntu.com maverick/restricted Sources            
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/main Sources                  
Hit http://archive.ubuntu.com maverick/multiverse Sources            
Hit http://archive.ubuntu.com maverick/universe Sources              
Hit http://archive.ubuntu.com maverick/main i386 Packages            
Hit http://archive.ubuntu.com maverick/restricted i386 Packages      
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages      
Hit http://archive.ubuntu.com maverick/universe i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/restricted Sources    
Hit http://archive.ubuntu.com maverick-updates/main Sources          
Ign http://download.skype.com stable/non-free Sources                
Ign http://ppa.launchpad.net maverick/main Sources                   
Ign http://ppa.launchpad.net maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages    
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://download.skype.com stable/non-free i386 Packages          
Err http://ppa.launchpad.net maverick/main Sources                   
  404  Not Found
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources   
Hit http://archive.ubuntu.com maverick-security/universe Sources     
Err http://download.skype.com stable/non-free Sources                
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages             
  404  Not Found
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Fetched 2,619B in 2s (1,298B/s)
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It's been happening for days for no reason I can think of :( Thanks in advance! 

P.S: I'm using 10.10

---

### Post by plucky on 2011-03-17
```
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

If you take the address [http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/maverick/main/source/Sources.gz) you will get the 404 error because it doesn't exist.

See [Here](http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/)

The Skype repository also is not there but leads to the Skype linux download page.

Open **Software Sources** and un-tick those sources and then run ```
sudo apt-get update
```

Good Luck

---

### Post by k3lt01 on 2011-03-17
Skype is available, I have it on my list and just tried my update and it worked without a hitch. Could you post your sources.list so we can see how it is formatted. You may have a bad entry that while it isn't being pick up by apt as being incorrect (which in itself is strange) may be causing your problem with skype.

My sources.list skype entry, along with some additional information, looks like this.
```
#### Skype - www.skype.com
## Run this command: gpg --keyserver pgp.mit.edu --recv-keys 0xd66b746e && gpg --export --armor 0xd66b746e  | apt-key add -
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

---

### Post by MotherMonster on 2011-03-17
Skype is already installed, I don't know why. But the problem is it tells me to check my internet connection when I have one.

---

### Post by k3lt01 on 2011-03-17
That is just a standard response if apt cannot locate something. Basically it is telling you to do some detective work to fix the issue.

Snark's advice to untick those repos will fix the problem but skype will not update if you do that, not that skype ever updates anyway.

If you compare the skype entry in your sources.list with mine it may give you a clue to part of the problem. If your not worried about going that far then just untick, or remove the entries altogether, and then an "apt-get update" will fix things for you. :)

---

