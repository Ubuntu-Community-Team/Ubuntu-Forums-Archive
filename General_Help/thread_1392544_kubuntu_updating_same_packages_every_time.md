---
title: "kubuntu updating same packages every time"
date: 2010-01-28
forum: General Help
---

### Post by rahulabc on 2010-01-28
I'm using kubuntu karmic on my computer. I hv a prob. frm some days that when I run "sudo apt-get update" or "sudo aptitude update", then it downloads same packages every time of 10.5 mb. I also recreated my sources.list file but it has same prob. again..

Plz help me...

---

### Post by rahulabc on 2010-01-29
This happens when I run apt-get update

```
Get:1 http://in.archive.ubuntu.com karmic Release.gpg [189B]
Ign http://in.archive.ubuntu.com karmic/main Translation-en_US                                                          
Ign http://in.archive.ubuntu.com karmic/restricted Translation-en_US                                                    
Ign http://in.archive.ubuntu.com karmic/universe Translation-en_US                                                      
Get:2 http://in.archive.ubuntu.com karmic-security Release.gpg [189B]                                                   
Ign http://in.archive.ubuntu.com karmic-security/main Translation-en_US                                                 
Ign http://in.archive.ubuntu.com karmic-security/restricted Translation-en_US                                           
Ign http://in.archive.ubuntu.com karmic-security/universe Translation-en_US                                             
Get:3 http://in.archive.ubuntu.com karmic-updates Release.gpg [189B]                                                    
Ign http://in.archive.ubuntu.com karmic-updates/main Translation-en_US                                                  
Ign http://in.archive.ubuntu.com karmic-updates/restricted Translation-en_US                                            
Ign http://in.archive.ubuntu.com karmic-updates/universe Translation-en_US                                              
Get:4 http://in.archive.ubuntu.com karmic Release [65.9kB]  
Hit http://ppa.launchpad.net karmic Release.gpg             
Get:5 http://in.archive.ubuntu.com karmic-security Release [44.1kB]                                                     
Get:6 http://in.archive.ubuntu.com karmic-updates Release [44.1kB]                                                      
Get:7 http://in.archive.ubuntu.com karmic/main Packages [1,353kB]                                                       
Ign http://ppa.launchpad.net karmic/main Translation-en_US  
Hit http://ppa.launchpad.net karmic Release.gpg             
Ign http://ppa.launchpad.net karmic/main Translation-en_US  
Hit http://ppa.launchpad.net karmic Release                 
Hit http://ppa.launchpad.net karmic Release                 
Hit http://ppa.launchpad.net karmic/main Packages           
Hit http://ppa.launchpad.net karmic/main Sources            
Hit http://ppa.launchpad.net karmic/main Packages           
Hit http://ppa.launchpad.net karmic/main Sources            
Get:8 http://in.archive.ubuntu.com karmic/restricted Packages [7,971B]                                                  
Get:9 http://in.archive.ubuntu.com karmic/universe Packages [5,133kB]                                                   
Get:10 http://in.archive.ubuntu.com karmic/main Sources [640kB]                                                         
Get:11 http://in.archive.ubuntu.com karmic/restricted Sources [3,270B]                                                  
Get:12 http://in.archive.ubuntu.com karmic/universe Sources [2,795kB]
Get:13 http://in.archive.ubuntu.com karmic-security/main Packages [59.7kB]
Get:14 http://in.archive.ubuntu.com karmic-security/restricted Packages [14B]
Get:15 http://in.archive.ubuntu.com karmic-security/universe Packages [23.2kB]
Get:16 http://in.archive.ubuntu.com karmic-security/main Sources [17.7kB]
Get:17 http://in.archive.ubuntu.com karmic-security/restricted Sources [14B]
Get:18 http://in.archive.ubuntu.com karmic-security/universe Sources [3,944B]
Get:19 http://in.archive.ubuntu.com karmic-updates/main Packages [160kB]
Get:20 http://in.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Get:21 http://in.archive.ubuntu.com karmic-updates/universe Packages [93.8kB]
Get:22 http://in.archive.ubuntu.com karmic-updates/main Sources [48.7kB]
Get:23 http://in.archive.ubuntu.com karmic-updates/restricted Sources [14B]
Get:24 http://in.archive.ubuntu.com karmic-updates/universe Sources [22.8kB]
Fetched 10.5MB in 16min 16s (10.8kB/s)
Reading package lists... Done

```

---

### Post by rahulabc on 2010-01-29
oh plz! can anyone help????

---

### Post by no2498 on 2010-01-29
? did you ever install the updates

---

### Post by billyboy1995 on 2010-01-29
That is the way it checks for updates. When it finds one it will ask you to input y or n for yes or no. So don't worry it is only downloading and replacing the old files.

---

### Post by snowpine on 2010-01-29
You need to:

```
sudo apt-get upgrade
```

to apply the changes. :)

---

### Post by raktarok on 2010-01-29
That is not a problem, actually. Those are not software packages but files that contain the list of packages available in the repositories. apt-get update is supposed to do that - fetch all the software lists, thus allowing you to install any package that has been recently updated/added in the repo. 

To clarify more, update just downlaods the lists, use upgrade to actually install the new packages.

So be happy, its not a problem!

---

### Post by rahulabc on 2010-01-29
ok thnx everyone.. :p

---

