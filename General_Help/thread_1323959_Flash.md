---
title: "Flash??????"
date: 2009-11-12
forum: General Help
---

### Post by knuckles1 on 2009-11-12
hi, i am completely new to linux and have recently installed ubuntu 9.10. I have found it really great compared to any windows system i have had before. For me it has taken some getting used to with the terminal and different ways of installing things. However i have learn how to do most things i need to do, apart from getting flash to work! I have used all methods i can find, including the adobe packages and their installation instructions, the mozilla plugin finder and those options, i have also followed others advice using the terminal root user flash nonfree thing and it says flash nonfree not found.. also the synaptic package manager does not find any "flash" when i search...  i am lost 100% i have NO idea how to install flash. I am sorry if i am not very good at explaining what i have tried as i forgot to write it down exactly and i am not familiar with this OS. does anyone know any good links to installing flash on a 32 bit Ubuntu 9.10?? or has anyone had this problem?? I would have used the absolute beginners forum but it said something about restrictions due to malicous commands. Thanks in advance if anyone can help... otherwise thanks for reading!

---

### Post by Wandel on 2009-11-12
I find the easiest way is to install ubuntu-restricted-extras.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by knuckles1 on 2009-11-12
I tried that and a popup kept saying "Could not find package 'ubuntu-restricted-extras'."

---

### Post by wojox on 2009-11-12
Open a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by BenAshton24 on 2009-11-12
```
sudo apt-get install flashplugin-nonfree
```

Ben.

---

### Post by knuckles1 on 2009-11-12
just tried and all i got was

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by knuckles1 on 2009-11-12
tried that too:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by wojox on 2009-11-12
Try :

```
sudo apt-get update
```

First

---

### Post by knuckles1 on 2009-11-12
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_AU 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_AU   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_AU 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources           
56% [Connecting to au.archive.ubuntu.com 

it seems to freeze at 56 %



On second try it says a whole bunch of w: failed to fetch.. http.............. 

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by wojox on 2009-11-12
Try going into System > Administration > Software Sources > Ubuntu Software

Click Download from: and choose a different server.

---

### Post by knuckles1 on 2009-11-12
Thanks heaps I did the different server... i chose "main " instead of Australia, and when it finished downloading about 75Mb of diff stuff i then did get install ubuntu-restricted-extras, then sudo apt-get install flashplugin- nonfree and viola it worked! Fantastic can't thank you enough mate

---

### Post by knuckles1 on 2009-11-12
*

---

