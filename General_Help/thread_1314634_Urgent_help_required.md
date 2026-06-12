---
title: "Urgent help required"
date: 2009-11-04
forum: General Help
---

### Post by amirmku on 2009-11-04
Hi,
I am currently using ubuntu 9.04 which was working fine upto now but I screwed up its sound. Want it back desperately...............
Initially my microphone in skype was not working, there I went to system >preferences> sound>device> audio conferencing> sound capture and have change to OSS from Alsa . thereafter only flickering sound can be heard no improvement even changing the settings back………… moreover whole system sounds got screwed dont know wht to do?:confused:
Please help

---

### Post by kelvin.illa on 2009-11-05
Do you have 'gnome-alsamixer' installed? I'm asking because I forgot if it was still in Jaunty since I'm already in Karmic. Back to the question: if it is, fire it up via terminal by typing "gnome-alsamixer." The window will appear; check the settings and find out if you can find what's wrong (if the settings there are actually the cause).

Ask away if you have questions. I can only help up to here given the information you've provided so far.

---

### Post by P4man on 2009-11-05
> **amirmku said:**
> Hi,
I am currently using ubuntu 9.04 which was working fine upto now but I screwed up its sound. Want it back desperately...............
Initially my microphone in skype was not working, there I went to system >preferences> sound>device> audio conferencing> sound capture and have change to OSS from Alsa . thereafter only flickering sound can be heard no improvement even changing the settings back&#8230;&#8230;&#8230;&#8230; moreover whole system sounds got screwed dont know wht to do?:confused:
Please help

Which versiom of skype are you using? If you are using the latest beta, then you should set pulseaudio as default mixer and for audio conferencing, and you might want to install *pavucontrol* to configure pulseaudio.

If you are using the previous version of skype, then it uses alsa instead of pulse and it will ignore anything you configure in preferences > sound afaik. You have to select the right device in skype itself and make sure the device is not muted (use gnome-alsamixer or just alsamixer from a terminal)

---

### Post by amirmku on 2009-11-05
Hi frends Problem solved, It appears when I was playing around with sound settings, PCM got down to minmum(zero), In terminal i typed 
alsamixer the terminal showed PCM to be zero.
Finally increasing the PCM i got sound back.

I have another problem of not being able download all repositories, When I tried upgrading it thru synaptic manager.................
Any suggestion

---

### Post by P4man on 2009-11-05
run 

sudo apt-get update

in a terminal and post the output here. Could just be a mirror that is offline or overloaded. Try  picking another one from system > administration > software sources.

---

### Post by amirmku on 2009-11-05
And regarding Skype, as far as I know I installed skype thru command **skype-static**. So I dont know what version of skype I am using . sorry for the negligence as I am new to ubuntu.
Any command for checking which version of skype I am having.
Moreover in test call every thing is fine except the microphone.

---

### Post by P4man on 2009-11-05
help / about should do the trick of revealing the skype version I imagine.
As for the mic not working, does it work in other apps like sound recorder?

You may have to experiment with the skype audio device settings and/or alsa mixer settings (mic boost, recording volume and on some cards you have more than 1 mic input and you need to select the right one. Cant give you exact instructions as im on karmic, but from memory I think you have to right click the volume control in the tray, select properties and then enable all the sliders in preferences.. something like that.

---

### Post by amirmku on 2009-11-05
Hi please find the output of sudo apt-get update


amir@ubuntu:~$ sudo apt-get update
[sudo] password for amir: 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) jaunty Release.gpg                             
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) jaunty/main Translation-en_US                  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Translation-en_US                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg [189B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US              
Get:5 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release.gpg [197B]                 
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Translation-en_US           
Get:6 [http://le-web.org](http://le-web.org) stable Release.gpg [197B]                              
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates Release.gpg                    
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Get:12 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Translation-en_US     
Get:13 [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Get:14 [http://dl.google.com](http://dl.google.com) stable Release [2540B]                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US            
Get:15 [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty Release [1723B]                       
Ign [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) jaunty Release                                 
Get:16 [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release [3454B]                   
Ign [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release                              
Get:17 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release [1019B]                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_US                      
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed Release                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) jaunty/non-free Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg                      
Get:21 [http://dl.google.com](http://dl.google.com) stable/main Packages [665B]                        
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Packages                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Ign [http://linux.getdropbox.com](http://linux.getdropbox.com) jaunty/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release.gpg [189B]            
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_US                
Get:23 [http://deb.opera.com](http://deb.opera.com) lenny Release [1067B]                              
Ign [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Translation-en_US           
Get:27 [http://people.apache.org](http://people.apache.org) cassandra/ Release.gpg                         
Get:28 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [1010B]                   
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) jaunty/main Packages                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US     
Hit [http://linux.getdropbox.com](http://linux.getdropbox.com) jaunty/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release                         
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-backports/partner Sources              
Get:31 [http://people.apache.org](http://people.apache.org) cassandra/ Translation-en_US                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release                          
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release [49.6kB]              
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-updates/partner Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-security/partner Sources               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty-proposed/partner Sources               
61% [32 Release 11324/49.6kB 22%] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://people.apache.org](http://people.apache.org) cassandra/ Translation-en_US                      
Ign [http://le-web.org](http://le-web.org) stable/main Translation-en_US                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Packages             
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Sources              
Get:43 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                   
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                   
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages              
Get:51 [http://people.apache.org](http://people.apache.org) cassandra/ Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources               
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Packages [53.0kB]        
Ign [http://people.apache.org](http://people.apache.org) cassandra/ Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:53 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:54 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Get:55 [http://le-web.org](http://le-web.org) stable Release [5316B]                                
Ign [http://le-web.org](http://le-web.org) stable Release                                           
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Packages [966B]    
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Packages [5614B]     
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Packages [14B]     
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Sources [21.8kB]         
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Sources [14B]      
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Sources [1933B]      
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Sources [14B]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:63 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:64 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:65 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:66 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:67 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:68 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:69 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Get:70 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:71 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:72 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:73 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.6kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:74 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:75 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:76 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Get:77 [http://people.apache.org](http://people.apache.org) cassandra/ Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                  
99% [77 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectibzip2: (stdin) is not a bzip2 file.
Err [http://people.apache.org](http://people.apache.org) cassandra/ Packages                               
  Sub-process bzip2 returned an error code (2)
Ign [http://le-web.org](http://le-web.org) stable/main Packages                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Get:78 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [9717B]              
Get:79 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources [2721B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Get:80 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [3276B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Get:81 [http://people.apache.org](http://people.apache.org) cassandra/ Sources                             
99% [81 Sources bzip2 0] [Waiting for headers] [Connecting to le-web.org (91.20bzip2: (stdin) is not a bzip2 file.
Err [http://people.apache.org](http://people.apache.org) cassandra/ Sources                                
  Sub-process bzip2 returned an error code (2)
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://le-web.org](http://le-web.org) stable/main Packages                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Fetched 362kB in 7s (49.1kB/s)                                                 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DA7581859566E92
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://people.apache.org](http://people.apache.org) cassandra/ Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: [http://le-web.org](http://le-web.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A423FD95416E75D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC1223EE2314809
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DA51AF64BD0ECAE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: Failed to fetch [http://people.apache.org/~eevans/debian/cassandra/Packages.bz2](http://people.apache.org/~eevans/debian/cassandra/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://people.apache.org/~eevans/debian/cassandra/Sources.bz2](http://people.apache.org/~eevans/debian/cassandra/Sources.bz2)  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
amir@ubuntu:~$

---

### Post by liquidbee on 2009-11-05
```
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

---

### Post by P4man on 2009-11-05
lol. you think you added enough repo's :)
anyway those warning at the end are just that you added a lot of repositories for which you didnt import their keys. You can still download from them but downloads can not be verified. Thats not a drama. Perhaps someone else can explain how to solve it (assuming ubuntu keyserver is no longer offline).
edit:see previous post :)

 Then the casandra repo for apache seems wrong or down, you might want to remove it from your software sources or at least uncheck it.

Other than that I see no problem that should prevent you from downloading or installing anything from the repo's. You will get warnings about the missing keys, but does it fail? If so with what error message?

edit: one more thing.. put such long outputs between [ code ] tags please :)

---

### Post by amirmku on 2009-11-05
> **P4man said:**
> help / about should do the trick of revealing the skype version I imagine.
As for the mic not working, does it work in other apps like sound recorder?

You may have to experiment with the skype audio device settings and/or alsa mixer settings (mic boost, recording volume and on some cards you have more than 1 mic input and you need to select the right one. Cant give you exact instructions as im on karmic, but from memory I think you have to right click the volume control in the tray, select properties and then enable all the sliders in preferences.. something like that.


Ya initially sounder recorder was working, But when I encountered problem with skype microphone, I tried checking sound recorder is working but tht is also not working.....................

---

### Post by amirmku on 2009-11-05
[IMG]http://file:///home/amir/Desktop/repository.jpg[/IMG]

Hi P4man,
The above is the screen shot which I get while downloading the repositories.
And as you mentioned the repository is too long can you please tell what all things to removed. 
And How to remove as I new to ubuntu. 
Thanks..

---

### Post by P4man on 2009-11-05
Meh, its not "too long". If you want to remove something, go to system > adminstration > software sources

go to the third party tab, and deselect or delete what you dont need. Frankly Id only delete or temporarily disable the apache repo which doesnt seem to work. 

As for the missing keys, I do not know an easy way to solve that. Generally when you add a repository to your software sources, the webpage will also give instructions how to import the key. Its a good idea to do that. Usually you just have to copy paste the provided command.

Lets take virtualbox as example, You probably added the repo after visiting this page:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

If you scroll down a bit further you will see > Sun public key for apt-secure can be downloaded here. You can add this key witt ....
or combine downloading and registering: 

Then a command which looks quite cryptic. But you dont have to understand it, just copy it,  open a terminal (or press alt f2) and paste the command in there:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

If you do that you will get an OK in the terminal and thats it. Next time you reload your repositories you will no longer get a warning for the missing key for virtualbox and anything you install from it (including updates to virtualbox) will be verified before its installed. That ensure the files have not been tampered with, and its mecahnisms such as this take make viruses and malware next to impossible on linux.

But you'll have to do that for each missing key if you want to eliminate these warning messages each time you try to install something. Either add the key, remove the repository or live with the warning message :)

---

### Post by amirmku on 2009-11-06
> **P4man said:**
> Meh, its not "too long". If you want to remove something, go to system > adminstration > software sources

go to the third party tab, and deselect or delete what you dont need. Frankly Id only delete or temporarily disable the apache repo which doesnt seem to work. 

As for the missing keys, I do not know an easy way to solve that. Generally when you add a repository to your software sources, the webpage will also give instructions how to import the key. Its a good idea to do that. Usually you just have to copy paste the provided command.

Lets take virtualbox as example, You probably added the repo after visiting this page:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

If you scroll down a bit further you will see 

Then a command which looks quite cryptic. But you dont have to understand it, just copy it,  open a terminal (or press alt f2) and paste the command in there:

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```If you do that you will get an OK in the terminal and thats it. Next time you reload your repositories you will no longer get a warning for the missing key for virtualbox and anything you install from it (including updates to virtualbox) will be verified before its installed. That ensure the files have not been tampered with, and its mecahnisms such as this take make viruses and malware next to impossible on linux.

But you'll have to do that for each missing key if you want to eliminate these warning messages each time you try to install something. Either add the key, remove the repository or live with the warning message :)



Thanks buddy I will try it................;)

---

