---
title: "Problem while loading Repository..."
date: 2010-10-18
forum: General Help
---

### Post by tajiknomi on 2010-10-18
[SIZE=2]*Recently i was about to installing **skype**, for that i have to check the repostory in the **software Source**...after that it shows me the message for **Reload*** and then it starts Downloading but at the last it shows me the message [/SIZE] 

"[B]Some index files failed to download, they have been ignored, or old ones used instead.
"[/B]
Moreover [SIZE=2]the pic is attached herewith...[/SIZE]

---

### Post by plucky on 2010-10-18
> **tajiknomi said:**
> [SIZE=2]*Recently i was about to installing **skype**, for that i have to check the repostory in the **software Source**...after that it shows me the message for **Reload*** and then it starts Downloading but at the last it shows me the message [/SIZE] 

"[B]Some index files failed to download, they have been ignored, or old ones used instead.
"[/B]
Moreover [SIZE=2]the pic is attached herewith...[/SIZE]

Open a terminal and (Applications > Accessories > Terminal)```
sudo apt-get update
``` and post the results to the forum.

> Moreover [SIZE=2]the pic is attached herewith...


??


Good Luck

---

### Post by tajiknomi on 2010-10-18
[SIZE=2][I]**The result is..**

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                      
Ign [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US

Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages          
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://pk.arch]("http://pk.archive.ubuntu.com")
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) lucid-updates/multiverse Sources
W: Failed to fetch [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: **Some index files failed to download, they have been ignored, or old ones used instead.**

[/I][/SIZE]

---

### Post by tajiknomi on 2010-10-18
[SIZE=2][I]oh sorry... i forgot Pic..

pic is here attached...
[/I][/SIZE]

---

### Post by plucky on 2010-10-18
> W: Failed to fetch [http://ppa.launchpad.net/danielgtayl...86/Packages.gz](http://ppa.launchpad.net/danielgtayl...86/Packages.gz) 404 Not Found

Open Software Sources and in the "Other Software" tab un-tick this ppa as a source,then reload and see if that fixes the problem.

Good Luck

---

### Post by tajiknomi on 2010-10-18
[SIZE=2][I]ya Brother..its Work..


thanks:P

but can i know y this give me error..?
or if in future i am going to install certain soft,which is must require that repository as a source, what can i do 4 that..?
[/I][/SIZE]

---

### Post by plucky on 2010-10-18
> but can i know y this give me error..?
or if in future i am going to install certain soft,which is must require that repository as a source, what can i do 4 that..?

Normally if the server is down you will get the 404 error.Also you can get it if the package archive doesn't exist when you have just upgraded to the next release.

It could also be the mirror you are using is being slow to be updated.

If you know the package server exists and it might be down,you can just un-tick the server as a source until a later time when it might be back up.

Good Luck

p.s Please mark as [SOLVED] using Thread Tools above.

---

### Post by tajiknomi on 2010-10-21
[SIZE=2]*thanks:P*[/SIZE]

---

