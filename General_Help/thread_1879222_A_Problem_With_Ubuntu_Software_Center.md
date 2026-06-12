---
title: "A Problem With Ubuntu Software Center"
date: 2011-11-11
forum: General Help
---

### Post by spoonatte on 2011-11-11
Im having problems with my software center .. when i want to install some package that followin message it appears
   
  
  **"items cannot be installed or removed until the package catalog is repaired. do you want to repair it now?"**
   
  
  after i click Repair, another window pops up, saying :
   
  
  **"Package operation fails - The installation or removal of a software package failed"**
   
  
    I click repair, and a few seconds later, it pops up again!!!! no matter how many times i click repair, nothing happens.
   
  
  Also .. I've Another Problem With Update Manager That Shows Me The Following Message:
   
  
  [B]"the package system is broken.
 Check if you are using third party repositories. If so disable them, since they are a common source of problems.
 Furthermore run the following command in a Terminal: apt-get install -f"[/B]
   
  
  Please provide a solution

---

### Post by matt_symes on 2011-11-11
Hi

Please use the default font !

We need to see the error messages from the software center to be able to help you. Please post them as they are not in your post #1.
 
**EDIT:** Thanks for updating your post #1.

Kind regards

---

### Post by matt_symes on 2011-11-11
Hi

Open a terminal and type

```
sudo apt-get install -f
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

Post back any errors here.

Kind regards

---

### Post by jackyboy633 on 2011-11-11
Have you run the command that Update Manager suggested. all you have to do is open up a terminal (Applications>Accessories>Terminal), then just copy and paste this command:

***sudo apt-get install -f***

You'll then need to enter your password.

Let me know how you get on!

Kind regards, Jackyboy633

---

### Post by matt_symes on 2011-11-11
Did two threads get merged there ? :confused:

---

### Post by nothingspecial on 2011-11-11
Please do not create multiple threads for one issue.

Merged.

---

### Post by spoonatte on 2011-11-11
Hééy, i Tried All The Solutions U've Told Me But Ntg Seems To Work

And Another Msg Appers :

Package operation failed
The installation or removal of a software package failed.
Details:
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 175949 files and directories currently installed.) 
Unpacking libuniconf4.6 (from .../libuniconf4.6_4.6.1-2build1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb (--unpack): 
 trying to overwrite '/etc/uniconf.conf', which is also in package libuniconf4.4 4.4.1-1.1 
Errors were encountered while processing: 
 /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: des problmes de dpendances empchent la configuration de wvdial: 
 wvdial dpend de libuniconf4.6; cependant: 
  Le paquet libuniconf4.6 n'est pas install. 
dpkg: erreur de traitement de wvdial (--configure): 
 problmes de dpendances - laiss non configur 
Des erreurs ont t rencontres pendant l'excution: 
 wvdial

---

### Post by spoonatte on 2011-11-12
When I Typed 
sudo apt-get update

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correction des dépendances... Fait
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  wine1.2-gecko
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  libuniconf4.6
Les NOUVEAUX paquets suivants seront installés :
  libuniconf4.6
0 mis à jour, 1 nouvellement installés, 0 à enlever et 34 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/126 ko dans les archives.
Après cette opération, 455 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
(Lecture de la base de données... 175949 fichiers et répertoires déjà installés.)
Dépaquetage de libuniconf4.6 (à partir de .../libuniconf4.6_4.6.1-2build1_i386.deb) ...
dpkg : erreur de traitement de /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb (--unpack) :
 tentative de remplacement de « /etc/uniconf.conf », qui appartient aussi au paquet libuniconf4.4 4.4.1-1.1
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correction des dépendances... Fait
Le paquet suivant a été installé automatiquement et n'est plus nécessaire :
  wine1.2-gecko
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  libuniconf4.6
Les NOUVEAUX paquets suivants seront installés :
  libuniconf4.6
0 mis à jour, 1 nouvellement installés, 0 à enlever et 34 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/126 ko dans les archives.
Après cette opération, 455 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? o
(Lecture de la base de données... 175949 fichiers et répertoires déjà installés.)
Dépaquetage de libuniconf4.6 (à partir de .../libuniconf4.6_4.6.1-2build1_i386.deb) ...
dpkg : erreur de traitement de /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb (--unpack) :
 tentative de remplacement de « /etc/uniconf.conf », qui appartient aussi au paquet libuniconf4.4 4.4.1-1.1
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1

And When I Typed 
sudo apt-get update Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric InRelease                             
Ign [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports InRelease                   
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric Release.gpg                       
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates Release.gpg               
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports Release.gpg             
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric Release                           
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates Release                   
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports Release                 
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/main Sources                      
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/restricted Sources                
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/universe Sources                  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/multiverse Sources                
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/main i386 Packages                
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/restricted i386 Packages          
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/universe i386 Packages            
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/multiverse i386 Packages          
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/main TranslationIndex             
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/multiverse TranslationIndex       
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/restricted TranslationIndex       
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/universe TranslationIndex         
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/main Sources              
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/restricted Sources        
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/universe Sources          
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/multiverse Sources        
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/main i386 Packages        
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/restricted i386 Packages  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/universe i386 Packages    
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/main TranslationIndex     
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/universe TranslationIndex 
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                    
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/main Sources            
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/restricted Sources      
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/universe Sources        
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/multiverse Sources      
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/main i386 Packages      
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources               
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/universe i386 Packages  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/main TranslationIndex   
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources         
Atteint [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                       
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/main Translation-fr               
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/main Translation-en               
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/multiverse Translation-fr         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages   
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages     
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages   
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex      
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/multiverse Translation-en         
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/restricted Translation-fr         
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/restricted Translation-en         
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/universe Translation-fr           
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric/universe Translation-en           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en        
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/main Translation-en       
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/multiverse Translation-en 
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/restricted Translation-en 
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-updates/universe Translation-en   
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/main Translation-en     
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en  
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Atteint [http://eh.archive.ubuntu.com](http://eh.archive.ubuntu.com) oneiric-backports/universe Translation-en 
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en    
Atteint [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                 
Atteint [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-fr_FR
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-fr
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-fr_FR
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-fr
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Reading package lists... Done

---

### Post by matt_symes on 2011-11-12
Hi

> Unpacking libuniconf4.6 (from .../libuniconf4.6_4.6.1-2build1_i386.deb) ...
 dpkg: error processing / var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb (- unpack):
 Trying to overwrite '/ etc / uniconf.conf' Which is Also in libuniconf4.4 package 4.4.1-1.1
 Errors Were Encountered while processing:
 / var/cache/apt/archives/libuniconf4.6_4.6.1-2build1_i386.deb
 Error in function:
 SystemError: E: Sub-process / usr / bin / dpkg Returned an error code (1)
 dpkg: problem of dependencies empchent configuring wvdial:
 wvdial dpend of libuniconf4.6, however:
 The package is not installed libuniconf4.6.
 dpkg: error processing wvdial (- configure):
 problem of dependencies - leaving unconfigured
 T have errors at run during meetings:
 wvdial

You need to install libuniconf4.6 

Kind regards

---

### Post by spoonatte on 2011-11-12
> **matt_symes said:**
> Hi



You need to install libuniconf4.6 

Kind regards


How ??

---

### Post by matt_symes on 2011-11-14
Hi

```
sudo apt-get install uniconfd
```

Kind regards

---

