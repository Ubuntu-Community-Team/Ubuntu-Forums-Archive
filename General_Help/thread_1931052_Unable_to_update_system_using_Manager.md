---
title: "Unable to update system using Manager"
date: 2012-02-24
forum: General Help
---

### Post by ronux on 2012-02-24
Hello all - 

My system: Ubuntu Maverick 10.10

I am coming across the following issue.
Go to Update Manager and I am unable to upgrade.
It gets stuck at Updating Cache (0B of 256B | in Details: 100% packages downloaded.

In terminal sudo apt-get update
I get a bunch of err and it gets stuck.

Also I am noticing that my weathers apps are unable to fecth data and they are stuck on ...updating...

I have full internet connectivity in spite of all this.
I tried on two distinct LANs and nothing changes (this should rule out that is a router issue).

Not sure what is impeding the connection for what I said above.
I had this happen in the past but it resolved with rebooting modem and router. Tried that too with no luck. 

I searched around and did not find anything close to my problem.
Any suggestion or feedback is very welcome.
Many thanks.

R.

---

### Post by 23dornot23d on 2012-02-24
Do 

**df **

in a terminal and post back the results please .....

also if you cut and paste can any errors that you see as they might help to tie it down to one thing

my initial thoughts are that the root partition may be full .... but without the errors

its hard to say .......

---

### Post by ronux on 2012-02-24
Command **df** (it seems that I have space...)
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            230577308  41025152 177839440  19% /
none                   2005104       268   2004836   1% /dev
none                   2011972       788   2011184   1% /dev/shm
none                   2011972       224   2011748   1% /var/run
none                   2011972         0   2011972   0% /var/lock

```
sudo apt-get update
``` I get the following.

```
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources/DiffIndex            
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/main Translation-en    
  Connection failed
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages/DiffIndex     
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/main Translation-en_US 
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                  
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/multiverse Translation-en
  Connection failed
Err [http://ppa.launchpad.net/docky-core/stable/ubuntu/](http://ppa.launchpad.net/docky-core/stable/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                  
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/multiverse Translation-en_US
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Err [http://ppa.launchpad.net/docky-core/stable/ubuntu/](http://ppa.launchpad.net/docky-core/stable/ubuntu/) maverick/main Translation-en_US
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/restricted Translation-en
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                  
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/restricted Translation-en_US
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/universe Translation-en
  Connection failed
Err [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-updates/universe Translation-en_US
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Err [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security Release.gpg                   
  Connection failed
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Err [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/main Translation-en   
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
  Connection failed
Err [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/main Translation-en_US
  Connection failed
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/multiverse Translation-en
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
  Connection failed
Err [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/) maverick/main Translation-en
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/multiverse Translation-en_US
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
  Connection failed
Err [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Err [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/restricted Translation-en
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/restricted Translation-en_US
  Connection failed
Err [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/) maverick/main Translation-en 
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/universe Translation-en
  Connection failed
Err [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Err [http://mirrors.cat.pdx.edu/ubuntu/](http://mirrors.cat.pdx.edu/ubuntu/) maverick-security/universe Translation-en_US
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick Release                                
Err [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates Release                        
Err [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security Release                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main Sources                           
Err [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted Sources                     
Err [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe Sources                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse Sources                     
Err [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main amd64 Packages                    
Err [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted amd64 Packages              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe amd64 Packages                
Err [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse amd64 Packages              
Err [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main Sources                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted Sources             
Err [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe Sources               
Err [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse Sources             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main amd64 Packages            
Err [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted amd64 Packages      
Err [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe amd64 Packages        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse amd64 Packages      
Err [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main Sources                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted Sources            
Err [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en_US
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe Sources              
Err [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse Sources            
Err [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main amd64 Packages           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted amd64 Packages     
Err [http://ppa.launchpad.net/videolan/master-daily/ubuntu/](http://ppa.launchpad.net/videolan/master-daily/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe amd64 Packages       
Err [http://ppa.launchpad.net/videolan/master-daily/ubuntu/](http://ppa.launchpad.net/videolan/master-daily/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse amd64 Packages     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main Sources                           
Err [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) maverick/main Translation-en
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted Sources                     
Err [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) maverick/main Translation-en_US
  Connection failed
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main amd64 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted amd64 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe amd64 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse amd64 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main amd64 Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe amd64 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main Sources                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse Sources            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main amd64 Packages           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted amd64 Packages     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe amd64 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse amd64 Packages     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main Sources                           
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted Sources                     
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe Sources                       
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse Sources                     
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/main amd64 Packages                    
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/restricted amd64 Packages              
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/universe amd64 Packages                
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick/multiverse amd64 Packages              
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main Sources                   
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted Sources             
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe Sources               
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse Sources             
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/main amd64 Packages            
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/restricted amd64 Packages      
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/universe amd64 Packages        
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-updates/multiverse amd64 Packages      
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main Sources                  
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted Sources            
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe Sources              
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse Sources            
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/main amd64 Packages           
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/restricted amd64 Packages     
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/universe amd64 Packages       
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Err [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) maverick-security/multiverse amd64 Packages     
  Connection failed
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages/DiffIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             q
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
  Connection failed
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
```

---

### Post by grahammechanical on 2012-02-24
Yeh, we get the picture. How long has this been happening? I notice that it is nearly all pps that are failing to update or are all of them ppa?

Could you try another mirror site? The server might be down for some reason.

Regards.

---

### Post by raja.genupula on 2012-02-24
yeah +1 .
to change the server go to update manager-> settings -> at 1st tab you see download from option , from there change your server some other best server and then try again . 

If you got any errors please post here .
Thank you .

---

### Post by ronux on 2012-02-24
No luck with different mirror site.
ppa - likely...
Same error message as I posted in previous section.

As I said earlier, it is a curious fact of my weather apps not working either. Coincidence? 

Thanks for your help!!

---

### Post by raja.genupula on 2012-02-24
no please post the output  here , some times what happen you know some PPA's are not going to available on that dist , so what we have to do is we need uncheck them and we can do that from either source list or update manager . 

so please post the output and whats the server you pick now ? 

if its not a main server then give try by switching to main server also .

All the best .

---

### Post by ronux on 2012-02-24
@Raja
After changing server to Main in Update Manager it asked me to reload and I got the following:

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg](http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Connection failed
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  Connection failed
Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Connection failed
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/Release.gpg)  Connection failed
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed
Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/maverick/free/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/maverick/non-free/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/dists/maverick/partner/source/Sources.gz)  Connection failed
Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.lzma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2)  
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/source/Sources.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/source/Sources.bz2)  
Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2)  
Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/source/Sources.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/source/Sources.bz2)  
Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2)  
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/source/Sources.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/source/Sources.bz2)  
Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/binary-amd64/Packages.bz2)  
Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  
Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/source/Sources.lzma)  
Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/binary-amd64/Packages.lzma)  
Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.lzma](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.lzma)  
Some index files failed to download, they have been ignored, or old ones used instead.

In terminal this:
> icted/i18n/Translation-en.bz2  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/dists/maverick/partner/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg](http://linux.dropbox.com/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://linux.dropbox.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg](http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/earth/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en.bz2](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/Release.gpg](http://packages.medibuntu.org/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/Release.gpg)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2)  Connection failed

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://linux.dropbox.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/maverick/free/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://packages.medibuntu.org/dists/maverick/non-free/binary-amd64/Packages.gz](http://packages.medibuntu.org/dists/maverick/non-free/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/dists/maverick/partner/source/Sources.gz)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/dists/maverick/partner/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/earth/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages.gz](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/docky-core/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/docky-core/stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/dr3mro/nautilus-actions-extra/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pellesimon/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/realtime.sunlight.wallpaper/rsw/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/videolan/master-daily/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/source/Sources.gz)  Connection failed

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Connection failed

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by raja.genupula on 2012-02-24
sounds like proxy issue, do you have any proxy settings ?

---

### Post by ronux on 2012-02-24
No...as I said I tried it on 2 different LANs. I have no proxy settings on my router. I have full internet connection.

---

### Post by audiomick on 2012-02-24
Hey Ronux.
You used quote tags in the last post. Try using the button with a hash on it.
#
That will give you code tags. That puts  a long output like that in a box with a scroll bar on the side.

---

### Post by ronux on 2012-02-24
Thx. I was not sure which of the codes was the one for the side bar. Sorry about that. I dislike those long inputs.

---

### Post by audiomick on 2012-02-24
> **ronux said:**
> Sorry about that. I dislike those long inputs.
No problem. We all had to learn. :) I think it took me about 20 minutes and editing a post about ten times to get it right.

---

### Post by ronux on 2012-02-24
My motto: live and learn!

Going back to my issue.
I ran CD Live on this machine and I was able to use manager update and terminal; interesting enough the weather app was working too.

I suspect that there is some corrupted file or maybe some specific setting (?) but I do not have enough ubuntu knowledge to pin point what it could be. 

Thanks.

---

### Post by ronux on 2012-02-28
I changed the mirror server to Main once and then to my country specific. I am able to reconnect but it is slow. I unchecked several PPAs to see if there was any improvement but it was not noticeable. 
I will close this issue as Solved.
For future reference and for those that come across similar issues I would suggest to change server (from either Update Manager - lower left corner Settings or from Ubuntu Software Center | Edit | Software Sources), wait and see. 
Double check with a different LAN in order to rule out any router / ISP issue on your end. 
Thanks.

---

