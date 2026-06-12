---
title: "help please  MAYA  INSTALLATION"
date: 2010-01-19
forum: General Help
---

### Post by larrysito on 2010-01-19
[COLOR=#000000][SIZE=2]**[SIZE=5]INSTALLING CRACK [/SIZE]**[/SIZE][/COLOR] 
 

 

 [COLOR=#000000][SIZE=2]**1.-     sudo mkdir /var/flexlm**[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]**2.-     cd /home/larry/obama**[/SIZE][/COLOR]
 

 [SIZE=2]**3.-     sudo cp aw.dat /var/flexlm/**[/SIZE]
 

 

   	 	 	 	 	 	   [SIZE=7]**Installing maya**[/SIZE]


  [SIZE=2]**1.- sudo apt-get install csh**[/SIZE]
 [SIZE=2]**2.- sudo apt-get install alien**[/SIZE]
 [SIZE=2]**3.- sudo alien -i --scripts ~/maya2009-linux/Maya2009_0_64-2009.0-452.x86_64.rpm**[/SIZE]


[SIZE=2][B]I MADE ALL THOSE STEPS MAYA IS LOADING BUT THE BOTOM "[COLOR=Red]ALT[/COLOR]" IS NOT WORKING AND I GOT THIS MESSAGE IN TERMINAL 
[/B][/SIZE]




Error: default temp directory /usr/tmp does not have write permissions.
*** Fatal Error: Failed creating directory: /usr/tmp



PLEASE I NEED HELP  :( 


[SIZE=2][/SIZE]

---

### Post by kiran001 on 2010-03-17
Hi friend 
I'm trying to install maya in ubuntu 9.10 and the maya version is 2009 i converted .rpm fies to .deb but i cant find maya package . Please help me on this if any body has maya 7,8 ,8.5 for linux can you please upload and share a link 

Thanks in advance

---

### Post by skibum3027 on 2010-04-16
You need to change the permissions for /usr/tmp

try this:
```
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
```

---

### Post by skibum3027 on 2010-04-16
> **kiran001 said:**
> Hi friend 
I'm trying to install maya in ubuntu 9.10 and the maya version is 2009 i converted .rpm fies to .deb but i cant find maya package . Please help me on this if any body has maya 7,8 ,8.5 for linux can you please upload and share a link 

Thanks in advance

Maya is not free software. Read forum rules and be careful what you post.

---

