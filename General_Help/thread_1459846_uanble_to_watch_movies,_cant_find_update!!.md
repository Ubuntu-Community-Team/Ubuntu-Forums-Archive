---
title: "uanble to watch movies, cant find update!!"
date: 2010-04-22
forum: General Help
---

### Post by facsimile on 2010-04-22
hey guys i need help again..
im not able to watch movies says that cant find pluins..

No packages with the requested plugins found
The requested plugins are:

MPEG-1 Layer 3 (MP3) decoder
DivX MPEG-4 Version 3 decoder

can somebody help me?:P

thanks!!!

---

### Post by r_s on 2010-04-22
install vlc , sudo apt-get install vlc

---

### Post by facsimile on 2010-04-22
facsimile@facsimile-desktop:~$ sudo apt-get install vlc
[sudo] password for facsimile: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc


this is what i get?:confused:

---

### Post by r_s on 2010-04-22
first try this
sudo apt-get update
sudo apt-get install vlc

---

### Post by facsimile on 2010-04-22
facsimile@facsimile-desktop:~$ sudo apt-get update
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US                     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                             
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg     
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Reading package lists... Done
facsimile@facsimile-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
facsimile@facsimile-desktop:~$ 



it still says the same thing...
thanks

---

### Post by r_s on 2010-04-22
system->administration->synaptic package manager
it will ask for you password, and then click on settings->repositories , check whether you have marked all your repositories or not. and then reload.

---

### Post by facsimile on 2010-04-22
THANKS!!!

IT WORKED YOUR GR:KS:KSEAT:guitar:

---

