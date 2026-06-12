---
title: "Update Manager never shows any new updates."
date: 2010-08-23
forum: General Help
---

### Post by fieryrage on 2010-08-23
It's been about 5 days since Ubuntu asked me to perform a Partial Upgrade and ever since then no new updates have been showing up in update manager and apt-get so I've been getting pretty paranoid. I used to get daily notifications of updates. 

So is there something wrong here?

Here's what I get when I do a sudo apt-get update, and I've tried changing mirrors.

```

Get:1 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_AU              
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_AU       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/ lucid/main Translation-en_AU
Ign http://apt.wxwidgets.org lucid-wx Release.gpg                              
Ign http://apt.wxwidgets.org/ lucid-wx/main Translation-en_AU                  
Get:2 http://dl.google.com stable Release [2,544B]                             
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/ lucid/main Translation-en_AU
Hit http://ppa.launchpad.net lucid Release                                     
Get:3 http://dl.google.com stable/main Packages [1,063B]                       
Ign http://apt.wxwidgets.org lucid-wx Release                                  
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://apt.wxwidgets.org lucid-wx/main Packages                            
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid/partner Sources                         
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://apt.wxwidgets.org lucid-wx/main Sources                             
Hit http://ppa.launchpad.net lucid/main Packages                              
Hit http://mirror.linux.org.au lucid Release.gpg                              
Hit http://mirror.linux.org.au/ubuntu/ lucid/main Translation-en_AU
Hit http://mirror.linux.org.au/ubuntu/ lucid/restricted Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid/universe Translation-en_AU
Hit http://mirror.linux.org.au/ubuntu/ lucid/multiverse Translation-en_AU
Hit http://mirror.linux.org.au lucid-updates Release.gpg
Ign http://mirror.linux.org.au/ubuntu/ lucid-updates/main Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-updates/restricted Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-updates/universe Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-updates/multiverse Translation-en_AU
Hit http://mirror.linux.org.au lucid-security Release.gpg
Ign http://mirror.linux.org.au/ubuntu/ lucid-security/main Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-security/restricted Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://mirror.linux.org.au/ubuntu/ lucid-security/multiverse Translation-en_AU
Hit http://mirror.linux.org.au lucid Release
Hit http://mirror.linux.org.au lucid-updates Release
Hit http://mirror.linux.org.au lucid-security Release
Hit http://mirror.linux.org.au lucid/main Packages
Hit http://mirror.linux.org.au lucid/restricted Packages
Hit http://mirror.linux.org.au lucid/main Sources
Hit http://mirror.linux.org.au lucid/restricted Sources
Hit http://mirror.linux.org.au lucid/universe Packages
Hit http://mirror.linux.org.au lucid/universe Sources
Hit http://mirror.linux.org.au lucid/multiverse Packages
Hit http://mirror.linux.org.au lucid/multiverse Sources
Hit http://mirror.linux.org.au lucid-updates/main Packages
Hit http://mirror.linux.org.au lucid-updates/restricted Packages
Hit http://mirror.linux.org.au lucid-updates/main Sources
Hit http://mirror.linux.org.au lucid-updates/restricted Sources
Hit http://mirror.linux.org.au lucid-updates/universe Packages
Hit http://mirror.linux.org.au lucid-updates/universe Sources
Hit http://mirror.linux.org.au lucid-updates/multiverse Packages
Hit http://mirror.linux.org.au lucid-updates/multiverse Sources
Hit http://mirror.linux.org.au lucid-security/main Packages
Hit http://mirror.linux.org.au lucid-security/restricted Packages
Hit http://mirror.linux.org.au lucid-security/main Sources
Hit http://mirror.linux.org.au lucid-security/restricted Sources
Hit http://mirror.linux.org.au lucid-security/universe Packages
Hit http://mirror.linux.org.au lucid-security/universe Sources
Hit http://mirror.linux.org.au lucid-security/multiverse Packages
Hit http://mirror.linux.org.au lucid-security/multiverse Sources
Fetched 3,796B in 4s (926B/s)
Reading package lists... Done
```and sudo apt-get upgrade just gets me this every time:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thanks in advance for any help.

---

### Post by richs-lxh on 2010-08-23
Don't worry about it, it's just that there are no updates/upgrades. I know it seems that there are updates every other day, but sometimes there's not much action in the repos.

If you are really worried that your local mirror isn't updating quick enough, try another repo. But I don't think ot's necessary.

---

### Post by fieryrage on 2010-08-23
Oh what a relief, thanks.

---

### Post by richs-lxh on 2010-08-23
I just checked mine which uses the French and Finnish mirrors, no updates for me either.

---

