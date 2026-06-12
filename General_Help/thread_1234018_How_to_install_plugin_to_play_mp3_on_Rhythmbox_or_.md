---
title: "How to install plugin to play mp3 on Rhythmbox or any other"
date: 2009-08-07
forum: General Help
---

### Post by ryansdistrict on 2009-08-07
hello i wana play mp3 but i need a plugin ort a small program that does so to download
any idea ??

---

### Post by credobyte on 2009-08-07
In terminal:
```
 
sudo apt-get install ubuntu-restricted-extras

```
 
It'll install media codecs and a few more useful utilities/tools ( flash player, support for .RAR archives, etc. ).

---

### Post by ryansdistrict on 2009-08-07
i did run this command and here is the output below is everything working ??
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras


what about the last thing 
E: Couldn't find package ubuntu-restricted-extras
is this something bad ??

thx and regards :)

---

### Post by ryansdistrict on 2009-08-07
btw i tried to play mp3 files still the codecs error apeparing

---

### Post by martinbaselier on 2009-08-07
Just follow this guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by credobyte on 2009-08-07
> **ryansdistrict said:**
> i did run this command and here is the output below is everything working ??
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
 
 
what about the last thing 
E: Couldn't find package ubuntu-restricted-extras
is this something bad ??
 
thx and regards :)
 
Update your apt database and try again.
 
```
sudo apt-get update
```

---

### Post by ryansdistrict on 2009-08-07
oh that was bit complex i searched for hte player couldnt find what to do 
please am bit dumb can u help me and tell me where to start ?

Thanks  in advance

---

### Post by ryansdistrict on 2009-08-07
okay credobyte ill give it a try

---

### Post by martinbaselier on 2009-08-07
If you follow the multimedia guide, it will solve your problem and help to prevent some future issues from occurring. (specific codecs not installed etc.)

---

### Post by ryansdistrict on 2009-08-07
the manual seams needs lots of downloads my internet speed doesnt allow me to download that much 

anyways credobyte i did what u told me to do  here is what i got 
Fetched 5577kB in 9min 27s (9818B/s)                                           
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ryansdistrict on 2009-08-07
Oops double posted it

---

### Post by credobyte on 2009-08-07
> **ryansdistrict said:**
> the manual seams needs lots of downloads my internet speed doesnt allow me to download that much 
 
anyways credobyte i did what u told me to do here is what i got 
Fetched 5577kB in 9min 27s (9818B/s) 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 
Another instance of aptitude is already running - the easiest way would be to restart your PC and try again by opening only 1 terminal window ( just to be sure that you've opened only 1 aptitude session ).

---

