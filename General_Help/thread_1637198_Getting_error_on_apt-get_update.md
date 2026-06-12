---
title: "Getting error on apt-get update"
date: 2010-12-04
forum: General Help
---

### Post by karthick87 on 2010-12-04
```
karthick@Ubuntu-desktop:~$ sudo apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg                                                                              
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ lucid/main Translation-en_IN                                 
Hit http://ppa.launchpad.net lucid Release.gpg                                                                              
Get:1 http://dl.google.com stable Release.gpg [197B]                                                                        
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN                                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN                                         
Hit http://archive.ubuntu.com lucid Release.gpg                                                                             
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN                                         
Hit http://deb.opera.com stable Release.gpg                                                                      
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_IN                                                
Hit http://download.virtualbox.org lucid Release.gpg                                                             
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN                                         
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_IN                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ lucid/main Translation-en_IN                              
Hit http://ppa.launchpad.net lucid Release.gpg                                                                              
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_IN                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/stefano-palazzo/stefano-testing/ubuntu/ lucid/main Translation-en_IN                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN                                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN                                 
Hit http://security.ubuntu.com lucid-security Release                                                                       
Hit http://ppa.launchpad.net lucid Release.gpg                                                                              
Ign http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu/ lucid/main Translation-en_IN                         
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN                                         
Hit http://archive.ubuntu.com lucid Release                                                                      
Hit http://deb.opera.com stable Release                                                                                     
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_IN                                      
Ign http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu/ lucid/main Translation-en_IN                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_IN                                             
Ign http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/user/ppa-name/ubuntu/ lucid/main Translation-en_IN                                  
Hit http://ppa.launchpad.net lucid Release                                                                       
Hit http://security.ubuntu.com lucid-security/restricted Packages                                                           
Hit http://ppa.launchpad.net lucid Release                                                                                  
Hit http://archive.ubuntu.com lucid/main Packages                                                                           
Ign http://deb.opera.com stable/non-free Packages                                                                           
Hit http://ppa.launchpad.net lucid Release                                                                       
Hit http://ppa.launchpad.net lucid Release                                                                                  
Hit http://ppa.launchpad.net lucid Release                                                                                  
Hit http://ppa.launchpad.net lucid Release                                                                                  
Hit http://ppa.launchpad.net lucid Release                                                                                  
Hit http://security.ubuntu.com lucid-security/main Packages                                                                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                                           
Hit http://security.ubuntu.com lucid-security/universe Packages                                                  
Hit http://ppa.launchpad.net lucid Release                                                                       
Ign http://ppa.launchpad.net lucid Release                                                                                  
Hit http://archive.ubuntu.com lucid/restricted Packages                                                                     
Hit http://archive.ubuntu.com lucid/main Sources                                                                 
Hit http://archive.ubuntu.com lucid/restricted Sources                                                           
Hit http://archive.ubuntu.com lucid/universe Packages                                                            
Hit http://archive.ubuntu.com lucid/universe Sources                                       
Hit http://archive.ubuntu.com lucid/multiverse Packages                                    
Hit http://download.virtualbox.org lucid Release                                                                 
Ign http://deb.opera.com stable/non-free Packages                                                                
Hit http://archive.ubuntu.com lucid/multiverse Sources                                     
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://download.virtualbox.org lucid/non-free Packages           
Hit http://deb.opera.com stable/non-free Packages                    
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Get:2 http://dl.google.com stable Release.gpg [189B]                                                                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN                                                
Get:3 http://dl.google.com stable Release [1,347B]                                                                          
Get:4 http://dl.google.com stable Release [1,338B]                                                                          
Get:5 http://dl.google.com stable/main Packages [1,081B]                                                                    
Get:6 http://dl.google.com stable/main Packages [613B]                                                                      
Fetched 4,765B in 10s (444B/s)                                                                                              
W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Can anyone help?

---

### Post by hiromato on 2010-12-04
W: Failed to fetch [http://ppa.launchpad.net/](http://ppa.launchpad.net/)[COLOR="Red"]user/ppa-name[/COLOR]/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

Have you perhaps added a ppa and forgotten to change the user and package name part?

What does you /etc/apt/sources.list look like?

---

### Post by karthick87 on 2010-12-04
Yes i have forgotten to change the username and package name..How to remove that entry?

---

### Post by hiromato on 2010-12-04
sudo gedit /etc/apt/sources.list

Then just delete the line, save and try sudo apt-get update again. 

If you're unsure about which line to remove, post the content of the file here and I'll help you spot it.

---

### Post by wojox on 2010-12-04
Try unchecking them through Software Sources: System->Administration->Software Sources->Other Software (Tab).

---

### Post by yetiman64 on 2010-12-04
System > Administration > Software Sources > Other Softtware tab, Detick (to disable the ppa) or remove (to permanently remove), click "close" then "reload". Rerun your updating to check all is OK.

Be very careful if you choose to edit sources.list (not recommended) as the above graphical proceedure edits this file anyway. Also if you manually edit please use gksudo as gedit is a graphical application.

---

### Post by karthick87 on 2010-12-04
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://download.virtualbox.org/virtualbox/debian lucid non-free
deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe

```

which entry do you want me to remove?

---

### Post by wojox on 2010-12-04
Read post 5 or 6. It's a ppa so it's not stored in /etc/apt/sources.list

---

### Post by karthick87 on 2010-12-04
Thank you i have removed the entry :)

---

