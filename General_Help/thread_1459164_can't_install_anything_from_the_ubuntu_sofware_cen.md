---
title: "can't install anything from the ubuntu sofware center!!!"
date: 2010-04-21
forum: General Help
---

### Post by chris.jericho on 2010-04-21
hey there fellows... yesterday I was trying to install Gnome Do and pidgin but I just couldn't install anything.....!!!

i don't know why but whenever I try to install anything I get an error message.

check out the screenshot... 

when I click okay... the installation just stops and this problem keeping repeating.!!!!!!!

Please HELP!!!!!!!!!!!!!

---

### Post by trig on 2010-04-21
wow that is strange.

---

### Post by evertmantel on 2010-04-21
Medibuntu, one of the repositories, is down ... the rumour is that it will be on line again somewhere today...

---

### Post by darolu on 2010-04-21
Seems like you added a new repository; you'll need to add the key to this repository; do you have the link you followed to install the repository? there's usually a link to get the key.

Edit: did you get it from here? [http://do.davebsd.com/wiki/Installing_Do#9.10_.28Karmic.29](http://do.davebsd.com/wiki/Installing_Do#9.10_.28Karmic.29)

Following the Karmic steps should work, you may need to do the "Add key" steps in the Jaunty Installation.

---

### Post by mcduck on 2010-04-21
> **chris.jericho said:**
> hey there fellows... yesterday I was trying to install Gnome Do and pidgin but I just couldn't install anything.....!!!

i don't know why but whenever I try to install anything I get an error message.

check out the screenshot... 

when I click okay... the installation just stops and this problem keeping repeating.!!!!!!!

Please HELP!!!!!!!!!!!!!

Based on the error you have added some additional software repository, but didn't add the PGP signing key for that repository. Without that, the packages from that source can't be verified.

If you have indeed added some repository recently, then simply add the GPG key for it as well and and the problem will be solved. Pretty much any decent repository should have both the GPG key and instructions for importing it somewhere available.

Also, like mentioned, the Madibntu repository is currently unavailable, although getting a error message about untrusted sources because of a missing repository doesn't seem correct to me.

Anyway, if you haven't added any repositories or you are sure you have also added the GPG keys for them, then please open a terminal and run "sudo apt-get update & post the output here so we can have a bit better look at what might be wrong...

---

### Post by chris.jericho on 2010-04-21
no screw that gnome do and other software... i haven't even installed them....

my microfone wasn't working... so some guy gave me fix for it... it was to add some lines to something using the terminal.....

the microfone started working but after that.... I just cannot install any software from the software center... can't understand whats the problemm...

please help me!!!

---

### Post by chris.jericho on 2010-04-21
> **mcduck said:**
> Based on the error you have added some additional software repository, but didn't add the PGP signing key for that repository. Without that, the packages from that source can't be verified.

If you have indeed added some repository recently, then simply add the GPG key for it as well and and the problem will be solved. Pretty much any decent repository should have both the GPG key and instructions for importing it somewhere available.

Also, like mentioned, the Madibntu repository is currently unavailable, although getting a error message about untrusted sources because of a missing repository doesn't seem correct to me.

Anyway, if you haven't added any repositories or you are sure you have also added the GPG keys for them, then please open a terminal and run "sudo apt-get update & post the output here so we can have a bit better look at what might be wrong...
hey bro,... i typed in sudo apt-get update..... this was the output

> 
chris@chris-desktop:~$ sudo apt-get update
[sudo] password for chris: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_IN              
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN    
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg [189B]            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release [57.2kB]                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release                         
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages [1,387kB]               
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [930B]                         
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]                        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]             
Get:10 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]                         
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_IN
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                         
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/main Translation-en_IN                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/restricted Translation-en_IN          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [2,992B]                   
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/universe Translation-en_IN            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Ign [http://debian.wgdd.de/ubuntu/](http://debian.wgdd.de/ubuntu/) jaunty/multiverse Translation-en_IN
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages [6,189B]
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources [659kB]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages                             
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources [3,761B]          
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages [5,450kB]          
Hit [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources [3,173kB]           
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages [175kB]          
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources [118kB]           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources              
Fetched 11.1MB in 1min 17s (143kB/s)                                           
Reading package lists... Done
chris@chris-desktop:~$ 


---

