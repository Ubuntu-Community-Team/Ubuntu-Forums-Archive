---
title: "Hardware Sensors Applet"
date: 2011-10-20
forum: General Help
---

### Post by uzzo2 on 2011-10-20
Does anyone know how to get an applet that will run in the new version of gnome? This is what I have since the upgrade to 11.10 because I didn't like unity. With the previous version, I had an applet that ran in the top panel all the time. It was out of my way and worked great, I can't seem to find one like that now. I found one called wmtemp, but it won't run in the panel, it's going to be on the screen in the way all the time.

---

### Post by haqking on 2011-10-20
> **uzzo2 said:**
> Does anyone know how to get an applet that will run in the new version of gnome? This is what I have since the upgrade to 11.10 because I didn't like unity. With the previous version, I had an applet that ran in the top panel all the time. It was out of my way and worked great, I can't seem to find one like that now. I found one called wmtemp, but it won't run in the panel, it's going to be on the screen in the way all the time.

xsensors still works in 11.10

[http://www.ubuntuupdates.org/packages/show/353245](http://www.ubuntuupdates.org/packages/show/353245)

---

### Post by uzzo2 on 2011-10-20
> **haqking said:**
> xsensors still works in 11.10

[http://www.ubuntuupdates.org/packages/show/353245](http://www.ubuntuupdates.org/packages/show/353245)
Will it run in a panel and be out of the way?

---

### Post by haqking on 2011-10-20
> **uzzo2 said:**
> Will it run in a panel and be out of the way?

well you cant add to the panel in 11.10 unless you use gnome classic and use gnome panel with alt+right click

I think ? ;-)

---

### Post by uzzo2 on 2011-10-20
> **haqking said:**
> well you cant add to the panel in 11.10 unless you use gnome classic and use gnome panel with alt+right click

I think ? ;-)
You were right, I thought you just had to right click on the panel before. But I don't see the applet I used to have for some reason, it's not listed.

---

### Post by haqking on 2011-10-20
> **uzzo2 said:**
> You were right, I thought you just had to right click on the panel before. But I don't see the applet I used to have for some reason, it's not listed.

yeah but if you install xsensors then you should get the option correct ?

I am shooting in the wind here by the way as i dont have my 11.10 VM up and running at the moment so sorry for guessing off top of head.

there is also a package for awn [http://www.ubuntuupdates.org/packages/show/327150](http://www.ubuntuupdates.org/packages/show/327150)

and see here [http://askubuntu.com/questions/66624/how-do-i-get-sensors-applet-working](http://askubuntu.com/questions/66624/how-do-i-get-sensors-applet-working)

---

### Post by uzzo2 on 2011-10-20
> **haqking said:**
> yeah but if you install xsensors then you should get the option correct ?

I am shooting in the wind here by the way as i dont have my 11.10 VM up and running at the moment so sorry for guessing off top of head.

there is also a package for awn [http://www.ubuntuupdates.org/packages/show/327150](http://www.ubuntuupdates.org/packages/show/327150)
 I did install xsensors, but it doesn't look like you can run it in the panel. I wish I could  remember what the one I had was called. It basically just had 3 sets of temp monitors that ran in the top panel. It had what looked like a thermometer beside each one. It would change colors from blue to yellow once you got above 45 degrees celcius.

---

### Post by haqking on 2011-10-20
> **uzzo2 said:**
> I did install xsensors, but it doesn't look like you can run it in the panel. I wish I could  remember what the one I had was called. It basically just had 3 sets of temp monitors that ran in the top panel. It had what looked like a thermometer beside each one. It would change colors from blue to yellow once you got above 45 degrees celcius.

if you mean the attached which i have running in 10.10 it is gnome sensors 2.2.5

---

### Post by uzzo2 on 2011-10-20
> **haqking said:**
> if you mean the attached which i have running in 10.10 it is gnome sensors 2.2.5
Exactly, can you make it work with this new gnome version?

---

### Post by haqking on 2011-10-20
> **uzzo2 said:**
> Exactly, can you make it work with this new gnome version?

Well thats what i said earlier, you cant add to the panel in 11.10.

I dont know if you can with session-fallback and classic with the gnome panel, you will need to try it or research it, i havent got my VM up and running to play with it at this minute but i will have a look later if you havent got it sorted

see here [http://reformedmusings.wordpress.com/2011/10/15/panel-hardware-sensors-in-ubuntu-unity-for-oneiric-11-10/](http://reformedmusings.wordpress.com/2011/10/15/panel-hardware-sensors-in-ubuntu-unity-for-oneiric-11-10/)

---

### Post by Linuxisfast on 2011-10-20
Best panel indicator is indicator-sensors and best of all, in systems with ACPI thermal management laptops, you don't need lm-sensors or hddtemp installed. You can install it via ppa at [https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily](https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily)

---

### Post by uzzo2 on 2011-10-20
> **haqking said:**
> Well thats what i said earlier, you cant add to the panel in 11.10.

I dont know if you can with session-fallback and classic with the gnome panel, you will need to try it or research it, i havent got my VM up and running to play with it at this minute but i will have a look later if you havent got it sorted

see here [http://reformedmusings.wordpress.com/2011/10/15/panel-hardware-sensors-in-ubuntu-unity-for-oneiric-11-10/](http://reformedmusings.wordpress.com/2011/10/15/panel-hardware-sensors-in-ubuntu-unity-for-oneiric-11-10/)
I was able to do it with the force quit application, it's there. I just don't see that hardware sensor applet.Psensors also works in a panel, you just have to minimize it. I just don't like it as well as the other one though.

---

### Post by larjan on 2011-10-20
your discription sounds like it could have been psensors. It is supposed to work in 11.10, but as I am still on 11.04, I don't know if it really does.

---

### Post by uzzo2 on 2011-10-20
> **Linuxisfast said:**
> Best panel indicator is indicator-sensors and best of all, in systems with ACPI thermal management laptops, you don't need lm-sensors or hddtemp installed. You can install it via ppa at [https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily](https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily)
I tried this one, it looks as if it did what it was supposed to do, but I either can't or don't know how to access it. Here's all of the output from the terminal.

You are about to add the following PPA to your system:
 Indicator Sensors Daily PPA
 
 More info: [https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily](https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.rRxMgUuPUK --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 81D64A6709CE7513F4F23790A9E15C2F2B944FEE
gpg: requesting key 2B944FEE from hkp server keyserver.ubuntu.com
gpg: key 2B944FEE: public key "Launchpad PPA for Alex Murray" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
phil@phil-desktop:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,776 B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [28.2 kB]           
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [652 B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [440 B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [16.8 kB]      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [14 B]   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [1,886 B]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [14 B]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [30.1 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [8,908 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [14 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [70 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [72 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [15.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease             
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Fetched 114 kB in 6s (16.5 kB/s)                                               
Reading package lists... Done

---

### Post by uzzo2 on 2011-10-20
> **larjan said:**
> your discription sounds like it could have been psensors. It is supposed to work in 11.10, but as I am still on 11.04, I don't know if it really does.
I don't think so, if you look at the thumbnail in post #8, that's exactly what I had installed before the upgrade.

---

### Post by Linuxisfast on 2011-10-20
> **uzzo2 said:**
> I tried this one, it looks as if it did what it was supposed to do, but I either can't or don't know how to access it. Here's all of the output from the terminal.

You are about to add the following PPA to your system:
 Indicator Sensors Daily PPA
 
 More info: [https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily](https://launchpad.net/~alexmurray/+archive/indicator-sensors-daily)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.rRxMgUuPUK --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 81D64A6709CE7513F4F23790A9E15C2F2B944FEE
gpg: requesting key 2B944FEE from hkp server keyserver.ubuntu.com
gpg: key 2B944FEE: public key "Launchpad PPA for Alex Murray" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
phil@phil-desktop:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,776 B]                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [28.2 kB]           
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [652 B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [440 B]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [16.8 kB]      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [14 B]   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [1,886 B]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [14 B]  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [30.1 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [8,908 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [14 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [70 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [72 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [15.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease             
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Fetched 114 kB in 6s (16.5 kB/s)                                               
Reading package lists... Done

```
sudo apt-get install indicator-sensors
```

alt+F2 type indicator-sensors and configure from panel.

---

### Post by uzzo2 on 2011-10-20
> **Linuxisfast said:**
> ```
sudo apt-get install indicator-sensors
```

alt+F2 type indicator-sensors and configure from panel.
Well it looks like it installed, but Alt+F2 doesn't do anything.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  indicator-sensors
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 2,000 B of archives.
After this operation, 32.8 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/alexmurray/indicator-sensors-daily/ubuntu/](http://ppa.launchpad.net/alexmurray/indicator-sensors-daily/ubuntu/) oneiric/main indicator-sensors i386 0.1-beta-0~89~oneiric1 [2,000 B]
Fetched 2,000 B in 0s (6,630 B/s)      
Selecting previously deselected package indicator-sensors.
(Reading database ... 173130 files and directories currently installed.)
Unpacking indicator-sensors (from .../indicator-sensors_0.1-beta-0~89~oneiric1_i386.deb) ...
Setting up indicator-sensors (0.1-beta-0~89~oneiric1) ...

---

