---
title: "Getting error on updating aptitude"
date: 2010-11-05
forum: General Help
---

### Post by karthick87 on 2010-11-05
```
karthick@Ubuntu-desktop:~$ sudo aptitude update
Hit http://in.archive.ubuntu.com lucid Release.gpg
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN                                                        
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN                                           
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN                                                  
Get:1 http://dl.google.com stable Release.gpg [189B]                                                                         
Hit http://ppa.launchpad.net lucid Release.gpg                                                                               
Ign http://ppa.launchpad.net/bisigi/ppa/ubuntu/ lucid/main Translation-en_IN                                                 
Get:2 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN                                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN                                           
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN                                             
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN                                                    
Hit http://security.ubuntu.com lucid-security Release                                                                        
Hit http://deb.opera.com stable Release.gpg                                                                                  
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_IN                                                            
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN                                                     
Hit http://download.virtualbox.org lucid Release.gpg                                                                         
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ lucid/main Translation-en_IN                                          
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_IN                          
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/stiff.ru/qmmp-releases/ubuntu/ lucid/main Translation-en_IN                         
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu/ lucid/main Translation-en_IN                        
Hit http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_IN                                              
Hit http://ppa.launchpad.net lucid Release                                                                                   
Hit http://security.ubuntu.com lucid-security/restricted Packages                                                            
Get:3 http://dl.google.com stable Release.gpg [189B]                                                                         
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN                                                  
Hit http://deb.opera.com stable Release                                                                                      
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_IN                                       
Get:4 http://in.archive.ubuntu.com lucid-updates Release.gpg [198B]                                              
Get:5 http://ppa.launchpad.net lucid Release [57.3kB]                                                                        
Hit http://ppa.launchpad.net lucid Release                                                                                   
Hit http://ppa.launchpad.net lucid Release                                                                                   
Hit http://ppa.launchpad.net lucid Release                                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                                   
Hit http://security.ubuntu.com lucid-security/main Packages                                                                  
Hit http://security.ubuntu.com lucid-security/multiverse Packages                                                            
Hit http://security.ubuntu.com lucid-security/universe Packages                                                              
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN                                                 
Get:6 http://dl.google.com stable Release [2,544B]                                                                           
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN                                          
Hit http://download.virtualbox.org lucid Release                                                                             
Hit http://ppa.launchpad.net lucid Release                                                                                   
Ign http://deb.opera.com stable/non-free Packages                                                                            
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN                                    
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN                                          
Get:7 http://dl.google.com stable Release [1,338B]                                                                           
Hit http://ppa.launchpad.net lucid/main Packages                                                                             
Hit http://ppa.launchpad.net lucid/main Packages                                                                             
Hit http://ppa.launchpad.net lucid/main Sources                                                                              
Hit http://ppa.launchpad.net lucid/main Packages                                                                             
Hit http://ppa.launchpad.net lucid/main Sources                                                                              
Hit http://ppa.launchpad.net lucid/main Packages                                                                             
Hit http://download.virtualbox.org lucid/non-free Packages                                                                   
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN                                            
Ign http://deb.opera.com stable/non-free Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                          
Hit http://in.archive.ubuntu.com lucid Release                                                      
Get:8 http://in.archive.ubuntu.com lucid-updates Release [44.7kB]                                                            
Get:9 http://dl.google.com stable/main Packages [1,082B]                                                                  
Hit http://ppa.launchpad.net lucid/main Packages                                                                     
Hit http://deb.opera.com stable/non-free Packages                                                                    
Get:10 http://dl.google.com stable/main Packages [613B]                   
Hit http://in.archive.ubuntu.com lucid/main Packages    
Hit http://in.archive.ubuntu.com lucid/restricted Packages
Hit http://in.archive.ubuntu.com lucid/main Sources
Hit http://in.archive.ubuntu.com lucid/restricted Sources
Hit http://in.archive.ubuntu.com lucid/universe Packages
Hit http://in.archive.ubuntu.com lucid/universe Sources
Hit http://in.archive.ubuntu.com lucid/multiverse Packages
Hit http://in.archive.ubuntu.com lucid/multiverse Sources
Get:11 http://in.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:12 http://in.archive.ubuntu.com lucid-updates/main Packages [339kB]       
Get:13 http://in.archive.ubuntu.com lucid-updates/multiverse Packages [7,373B]                                               
Get:14 http://in.archive.ubuntu.com lucid-updates/universe Packages [146kB]                                                  
Fetched 547kB in 14s (38.3kB/s)                                                                                              
Reading package lists... Done
[COLOR=Red]W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775[/COLOR]

```


What is it..?

---

### Post by sikander3786 on 2010-11-05
Re-import the GPG key for that launchpad PPA. See a workaround here.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

If you don't need that PPA any more, disable it from Software Sources.

---

### Post by karthick87 on 2010-11-05
What are the use of those GPG Keys.

---

### Post by sikander3786 on 2010-11-05
> **getyourkarthick said:**
> What are the use of those GPG Keys.
Some kind of digital signatures or say authentication key to authenticate the package is from trusted sources.

---

### Post by oldos2er on 2010-11-05
> **getyourkarthick said:**
> What are the use of those GPG Keys.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication) Tab

You can run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1E5D5E8D66AE0775
``` to install the key.

---

### Post by karthick87 on 2010-11-05
My problem solved,i ran
```
sudo launchpad-getkeys
```

---

### Post by deesto on 2010-11-08
I had a similar warning related to a different key, and oldos2er's instructions to re-import the offending key worked for me.

getyourkarthick, where did you get `launchpad-getkeys` from?  I don't seem to have that binary on my system.

---

### Post by karthick87 on 2010-11-08
> **deesto said:**
> I had a similar warning related to a different key, and oldos2er's instructions to re-import the offending key worked for me.

getyourkarthick, where did you get `launchpad-getkeys` from?  I don't seem to have that binary on my system.


Install launchpad-getkeys:

```
sudo apt-get install launchpad-getkeys
```

---

### Post by deesto on 2010-11-09
Yes; thanks: I know how to install packages.  I was asking what repository it's from, as it's not available on my system and can't be installed using the default channels.
```
$ aptitude show launchpad-getkeys
E: Unable to locate package launchpad-getkeys
$ sudo apt-get install launchpad-getkeys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package launchpad-getkeys
```

---

### Post by karthick87 on 2010-11-10
> **deesto said:**
> Yes; thanks: I know how to install packages.  I was asking what repository it's from, as it's not available on my system and can't be installed using the default channels.
```
$ aptitude show launchpad-getkeys
E: Unable to locate package launchpad-getkeys
$ sudo apt-get install launchpad-getkeys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package launchpad-getkeys
```


Check out the links below it may help you:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication)
[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

