---
title: "global menu in maverick desktop environment"
date: 2010-12-05
forum: General Help
---

### Post by rvchari on 2010-12-05
hello guys,
i am using maverick (netbook as well as desktop editions). netbook edition comes with global menu by default and i wish to have a global menu in desktop edition. this will keep me away from viewing bulky left panel in netbook edition which really looks ugly...
any help og how to get global menu running in desktop edition?
your help will help me keep my desktop cute !!!;)

---

### Post by sikander3786 on 2010-12-05
Add the global menu repository,

```
sudo add-apt-repository ppa:user/ppa:gnome2-globalmenu/ppa
```

Install global menu.

```
sudo apt-get update && sudo apt-get install gnome-applet-globalmenu
```

Right click top panel > Add to panel > Global menu ;-)

---

### Post by rvchari on 2010-12-05
hey buddy,
i am getting an error code as displayed by the screen shot. i tried terminal mode as well as synaptic package manager mode. i am enclosing the details....
any probs from my side ?

i wish to remind that ubuntu netbook edition and desktop edition both r installed.... and i wish to have a choice while booting. so i felt a global menu in desktop will be more presentable.

thanks in advance

---

### Post by sikander3786 on 2010-12-05
Were you able to install packages prior to this? Please post the output of these commands. (Text, not screenshot)

```
sudo apt-get check
```

```
sudo dpkg --configure -a
```

You can wrap your output with code tags # from post menu to make it easier to read. [/code] at the end [code] at the beginning.

---

### Post by rvchari on 2010-12-05
i did not install earlier...
i m attaching the output as u said...

---

### Post by sikander3786 on 2010-12-05
Seems like the directory /var/cache/debconf is missing. Try creating that.

```
sudo mkdir /var/cache/debconf
```

And try this one again.

```
sudo dpkg --configure -a
```

You can copy/paste the text from Terminal and it is easier to read ;-)

Please post text instead of screenshots.

Thanks.

---

### Post by rvchari on 2010-12-05
rvchari@maverick-meerkat:~$ cd /var/cache
rvchari@maverick-meerkat:/var/cache$ ls
apt      flashplugin-installer  jockey    PackageKit
binfmts  fontconfig             ldconfig  samba
cups     hald                   man       system-tools-backends
rvchari@maverick-meerkat:/var/cache$ mkdir debconf
mkdir: cannot create directory `debconf': Permission denied
rvchari@maverick-meerkat:/var/cache$ sudo mkdir debconf
[sudo] password for rvchari: 
rvchari@maverick-meerkat:/var/cache$ cd
rvchari@maverick-meerkat:~$ sudo dpkg --configure -a
Setting up man-db (2.5.7-4) ...
Updating database of manual pages ...
rvchari@maverick-meerkat:~$

---

### Post by rvchari on 2010-12-05
package is successfully re-installed... (i hope so) as i didnt get any error msgs. still the damn applet doesnt show up in the "Add to Panel list":(

---

### Post by sikander3786 on 2010-12-05
Yes it seems like the error is gone.

What is the output of this one?

```
sudo apt-get update && sudo apt-get install gnome-applet-globalmenu
```

---

### Post by rvchari on 2010-12-05
rvchari@maverick-meerkat:~$ sudo apt-get update && sudo apt-get install gnome-applet-globalmenu
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                          
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en                                                                                     
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]                                                                                                     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                                                                                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                                               
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg [198B]                                                                                                
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                        
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                            
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                                                          
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_IN                                                       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en                                                                             
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en_IN                                                                          
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                                                                                  
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_IN                                                                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                                                      
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en                                      
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en_IN                                                                        
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                                            
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                                                     
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN                                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                                                                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                                                               
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                                                                                                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                                                         
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN                                                                         
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg [198B]                                                                                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                                              
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en_IN                                                                     
Get:13 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [613B]                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                    
Ign [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Ign [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Connection failed
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                   
  404  Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 4,577B in 10min 41s (7B/s)
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
rvchari@maverick-meerkat:~$ sudo apt-get update && sudo apt-get install --fix-missing gnome-applet-globalmenu
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                          
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                                         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                            
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                                                          
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg [198B]                                                                                                
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_IN                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                        
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN                                                                    
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                                                                                              
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en                                                                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                             
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [613B]                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN             
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en_IN                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                        
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                        
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN                                                                              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en                                                                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                   
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en_IN              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release                                                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            [
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages             
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages               
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages             
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en
99% [Waiting for headers] [Waiting for headers]^C                          
rvchari@maverick-meerkat:~$

---

### Post by rvchari on 2010-12-05
rvchari@maverick-meerkat:~$ sudo apt-get update && sudo apt-get install gnome-applet-globalmenu
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                          
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en                                                                                     
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]                                                                                                     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                                                                                
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                                               
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg [198B]                                                                                                
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                        
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                               
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                                                            
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                                                          
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_IN                                                       
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en                                                                             
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en_IN                                                                          
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                                                                                  
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_IN                                                                               
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                                                      
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en                                      
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en_IN                                                                        
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                                            
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                                
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]                                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                                                     
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN                                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                                                                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                                                               
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                                                                                                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                                                         
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en                                                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN                                                                         
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg [198B]                                                                                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                                              
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en_IN                                                                     
Get:13 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [613B]                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                                    
Ign [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Ign [http://ppa.launchpad.net/user/ppa/ubuntu/](http://ppa.launchpad.net/user/ppa/ubuntu/) maverick/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Connection failed
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                   
  404  Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 4,577B in 10min 41s (7B/s)
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
rvchari@maverick-meerkat:~$ sudo apt-get update && sudo apt-get install --fix-missing gnome-applet-globalmenu
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                          
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                                                                                                         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                            
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                                                          
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg [198B]                                                                                                
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_IN                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                                                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                         
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                                        
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_IN                                                                    
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                                                                                              
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en                                                                 
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                                             
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [613B]                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                                                                                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                                                          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                                  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN             
Ign [http://ppa.launchpad.net/awn-testing/ppa/ubuntu/](http://ppa.launchpad.net/awn-testing/ppa/ubuntu/) maverick/main Translation-en_IN                
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                   
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN                      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                           
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN                        
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                        
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                                   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN                                                                              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                 
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en                                                                          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                   
Ign [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en_IN              
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release                                                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources                                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            [
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages             
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages               
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages             
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http:
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) maverick/main Translation-en
99% [Waiting for headers] [Waiting for headers]^C                          
rvchari@maverick-meerkat:~$

---

### Post by rvchari on 2010-12-05
thanks a ton buddy...
i got it. i was so frustrated, i gave a reboot.... and there it was !!!!
wonder if some one can help configure fire fox and open office in global menu !!!

---

### Post by rvchari on 2010-12-05
why does nautilus display as Desktop on global menu ? any config is needed ?

---

### Post by sikander3786 on 2010-12-05
Nautilus also displays as Desktop on my system and I have never bothered that ;-)

Glad to know you got it working anyway.

But there are a few errors in your apt-get update output. Post the output of this command if you want them to be corrected as well.

```
cat /etc/apt/sources.list
```

---

### Post by rvchari on 2010-12-05
rvchari@maverick-meerkat:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
rvchari@maverick-meerkat:~$ 


the prev list u asked took so long that i was impatient and i hit ctrl c which u might ve recognised...
nyways here is the one u asked for.

last but not the least.... i must say UBUNTU ROCKS !!!
finally do advise me on how to make this thread show as [solved] so it mite b useful to guys who r novice like me !!! and still lov to use ubuntu !!!

---

### Post by rvchari on 2010-12-05
talking of errors, i dont know what went wrong... last 2 days ubuntu gives an error while booting and i have to start using recovery mode.... wonder why...
i was so proud that my maverick boots so fast and shuts down equally faster.

now it seems to take ages to get it booted as well as shut down !!!!

your piece of advice in this regard will also be of gr8 help !!!

---

### Post by sikander3786 on 2010-12-05
Sources.list seems ok. Those errors are coming from Launchpad PPAs. If you wan't to get rid of those errors, disable all the Launchpad PPAs from Software Center > Edit > Software Sources > Other Software Tab and do apt-get update again.

Regarding the graphics issue, it might help to reconfigure your graphics settings.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot and see if the graphics get better.

If not, it would be better to start a new thread under the appropriate sub-forum with all the information like graphics card, proprietary drivers etc.

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by rvchari on 2010-12-05
error is not in grafix part. it gives a return msg saying /dev/sda5 (my root file sys) needs to be checked check forced.. then it finally returns a msg saying errors not corrected, needs to be checked.. !!! everything works fine but this dumb msg is irritating !!!

when i give a reboot, it boots fine but with delay... to get my gui login screen

---

### Post by sikander3786 on 2010-12-05
Run fsck from Live CD and try to correct the errors, otherwise, New Thread ;-)

```
fsck /dev/sda5
```

---

### Post by rvchari on 2010-12-05
thanks again buddy, was wondering how to workaround from within the linux box, my live cd is given to my kith and kin to make them experience        maverick !!!

will have to burn another cd, and then i ll do that !!!

---

### Post by rvchari on 2010-12-05
khuda haafiz....
will catch up later and who knows i may even ask you for more on my ubuntu trouble shooting !!!! this is where open source wins !!! GATES shut for MS ?

---

