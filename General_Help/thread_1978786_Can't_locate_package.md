---
title: "Can't locate package"
date: 2012-05-12
forum: General Help
---

### Post by Nando88 on 2012-05-12
sudo apt-get install can't locate package in E:, it doesn't install it from the internet.
I'm using lubuntu under virtual box,. 
How can I fix this?

---

### Post by sikander3786 on 2012-05-12
Rebuild the package index by running:

```
sudo apt-get update
```

Before you try to install any packages.

---

### Post by Nando88 on 2012-05-12
I already tried using sudo apt-get update, but even though it updates, I can't install the package after updating, it says: can't locate package in E:

---

### Post by sikander3786 on 2012-05-12
In that case, please post the complete output of apt-get update command and also let us know which package are you actually trying to install.

Thanks.

---

### Post by Bucky Ball on 2012-05-12
What package are you trying to install? That is a vital piece of info.

> **sikander3786 said:**
> In that case, please post the complete  output of apt-get update command and also let us know which package are  you actually trying to install.

Thanks.

+1.

---

### Post by Nando88 on 2012-05-12
nando@nando:/media/sf_nando/Downloads/glibc-2.15$ sudo apt-get install glibc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glibc
I'm trying to install glibc 2 (libc.so.6)

---

### Post by sikander3786 on 2012-05-12
> **Nando88 said:**
> nando@nando:/media/sf_nando/Downloads/glibc-2.15$ sudo apt-get install glibc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glibc
I'm trying to install glibc 2 (libc.so.6)
First of all, there isn't any package named 'glibc' exactly. Related one's are here:

[http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=all&section=all)

If you had posted the output of 'apt-get update' command, I could find if the 'universe' repository, which contains the 'glibc' related packages, is enabled on your system or not.

For now, go to Software Center > Edit > Software Sources and make sure the 'universe' repository is enabled. If it isn't, enable it run 'apt-get update' and then try to install the package.

If it is already enabled, please provide us the information we have been asking for. The output of:

```
sudo apt-get update
```

---

### Post by sikander3786 on 2012-05-12
Just noticed this:

```
nando@nando:/media/sf_nando/[COLOR="Red"]Downloads/glibc-2.15[/COLOR]$
```

So you are probably trying to compile it yourself, right? As mentioned above, a package named 'glibc' doesn't exist in the repositories. However, there is a package named 'glibc-source' but I am not sure what it does.

If you need to compile glibc yourself, look for a file named 'install' in the extracted package directory that you manually downloaded from somewhere.

Actually, installing packages from the repositories is recommended for security and also for auto-updates. In this case. And if you are new to this, compiling software isn't that easy.

---

### Post by Nando88 on 2012-05-12
sudo apt-get update:
nando@nando:~$ sudo apt-get update
[sudo] password for nando: 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done

---

### Post by sikander3786 on 2012-05-12
Ok, the 'universe' repository is enabled there. But there isn't any package named 'glibc' which you are trying to install. And as I mentioned earlier, I don't know what is that. You may probably wait for someone else to jump in and guide you with the installation of 'glibc'. Or have a look at the 'glibc-source' package.

---

### Post by Nando88 on 2012-05-12
I'm trying to install a gnu c library
[http://sourceware.org/ml/libc-alpha/2012-03/msg00836.html](http://sourceware.org/ml/libc-alpha/2012-03/msg00836.html)
but I need glibc 2 (libc.so.6) library -> this is the library I'm trying to install

---

### Post by Nando88 on 2012-05-12
I found that what I'm trying to install is also known as libc.so.6 and I need it for lubuntu 12.04 i386

---

### Post by Nando88 on 2012-05-12
I tried: 
sudo ln -s /lib/i386-linux-gnu/libc.so.6 /lib/libc.so.6
and then I tried to install labview 2009 and it said: 
./INSTALL: 101: ./INSTALL: [[: not found
glibc      Version cannot be determined 
./INSTALL: 101: ./INSTALL: [[: not found
Unpacking install files to /tmp/NI4882-2.5.1f0.install...
./INSTALL: 995: ./INSTALL: let: not found
./INSTALL: 996: ./INSTALL: let: not found
./INSTALL: 998: ./INSTALL: let: not found
./INSTALL: 551: ./INSTALL: [[: not found
There is insufficient free disk space to unpack the files.

Installer is aborted.

---

### Post by Bucky Ball on 2012-05-12
Do a search in Software Centre or Synaptics for 'libc.so.6'.

In Synaptics I didn't find that but when I entered it as the search I found a couple of libraries that probably contain it ...

---

