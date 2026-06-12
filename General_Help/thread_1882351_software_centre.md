---
title: "software centre"
date: 2011-11-17
forum: General Help
---

### Post by coffeebeankat on 2011-11-17
Hi all im very new here and also new to Ubuntu, learning each day. i have recently installed 11.10 onto a friends pc which was a clean install on a wiped drive using as a primary os. The problem i have is that the software centre simply wont open, it flashes when the icon is clicked but then nothing. please what can i do to fix. please understand im not very literate in this os as im a windows user primarily so if help can be explained in simple terms thats would be great.

thanks

---

### Post by WasMeHere on 2011-11-17
Hi coffeebeankat,

Welcome to the Ubuntu Forums :-)

If you cannot find it via the graphical user interface you can start a terminal (text window) with the key combination ***ctrl + alt + t*** and type
```
software-center
``` Finish with the Enter key!
If the program does not start, install it from the repositories with
```
sudo apt-get install software-center
```

Have fun finding out about Ubuntu
Olle

---

### Post by philinux on 2011-11-17
> **coffeebeankat said:**
> Hi all im very new here and also new to Ubuntu, learning each day. i have recently installed 11.10 onto a friends pc which was a clean install on a wiped drive using as a primary os. The problem i have is that the software centre simply wont open, it flashes when the icon is clicked but then nothing. please what can i do to fix. please understand im not very literate in this os as im a windows user primarily so if help can be explained in simple terms thats would be great.

thanks

As in post 2 open a terminal and run this

sudo apt-get update

Post back any errors and then run

sudo apt-get upgrade

---

### Post by coffeebeankat on 2011-11-23
hi sorry for my delay in returning here. I have used the code and im getting some errors back 

get install software-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package software-centre
newowner@pc-MS-6378-Invalid-entry-length-2-DMI-table-is-broken-Stop:~$ 
ewowner@pc-MS-6378-Invalid-entry-length-2-DMI-table-is-broken-Stop:~$ sudo apt-get install software-centre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package software-centre
newowner@pc-MS-6378-Invalid-entry-length-2-DMI-table-is-broken-Stop:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en
Reading package lists... Done
newowner@pc-MS-6378-Invalid-entry-length-2-DMI-table-is-broken-Stop:~$ 

i tried a couple of times but still get same result.
what do i do now ???:confused:

---

### Post by coffeebeankat on 2011-11-28
hello can anyone help me on the above problem? i really have no idea what to do :(

---

### Post by scarleo on 2011-11-28
Check your spelling, you typed 'software-centre' it's supposed to be 'software-center'

---

### Post by coffeebeankat on 2011-11-28
omg yes so i have, this is my dyslexia. i will give it another go and let you know if it works out.:D

---

