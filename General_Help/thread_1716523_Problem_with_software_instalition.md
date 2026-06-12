---
title: "Problem with software instalition"
date: 2011-03-28
forum: General Help
---

### Post by BluDawg on 2011-03-28
I can not add any software from the Unbuntu software center. I am running 10.04  here is a screen shot of the pop-up msg I get for every piece of soft ware.
[ATTACH]187406[/ATTACH]
This is a new problem, and I don't have a clue.

---

### Post by matt_symes on 2011-03-28
Hi

It sounds like you are missing some keys. Open a terminal and type

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen. This is normal.

Post the results back here.

Kind regards

---

### Post by BluDawg on 2011-03-28
This is the result from terminal after executing the update command 
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US           
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                      
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                            
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Fetched 189B in 11s (16B/s)                                                    
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

I rebooted and tried to install a piece of software and was greeted with the same result as the previous attempt.

---

### Post by matt_symes on 2011-03-28
Hi

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

That does not look right at all.  Open a terminal and type

```
cat /etc/apt/sources.list
```

Please post this between code tags. To use code tags hightlight the  text you want to put in code tags and hit the # button on the  panel just above where you are typing your reply. 

Kind regards

---

### Post by BluDawg on 2011-03-28
ok this is what I get 
```
desktop:~$ cat /ect/apt/sources.list
cat: /ect/apt/sources.list: No such file or directory
```

---

### Post by matt_symes on 2011-03-28
Hi

> **BluDawg said:**
> ok this is what I get 
```
desktop:~$ cat /**ect**/apt/sources.list
cat: /ect/apt/sources.list: No such file or directory
```

That should be 

```
cat /**etc**/apt/sources.list
```

Kind regards

---

### Post by BluDawg on 2011-03-28
It looks like the same code to me.:confused:

---

### Post by Enigmapond on 2011-03-28
No you entered ect...try it again with ETC (lowercase)or just copy this: cat /etc/apt/sources.list and paste in terminal

---

### Post by matt_symes on 2011-03-28
Hi

You typed

```
cat /**ect**/apt/sources.list
```

It should be 

```
cat /**etc**/apt/sources.list
```

**etc** and not **ect**. The c and the t are the wrong way around.

If you post the output we can fix the file :)

Kind regards

---

### Post by BluDawg on 2011-03-30
Sometimes life just gets in the way sorry It has taken me so long to  get back. thanks for pointing out my dyslexia. :redface: Anyway this is the result from the terminal
```
desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by 3Miro on 2011-03-30
Have you tried updating today, there may  have been a temporary issue with the server.

If still fails, then it seems the problem is somewhere else.

Go to System -> Admin -> Synaptic Package Manager, then select Settings -> Repositories. What do you have under "Other Software". One of those is probably blocking the updates, you should uncheck the wrong one.

---

### Post by BluDawg on 2011-03-30
> **3Miro said:**
> Have you tried updating today, there may  have been a temporary issue with the server.

If still fails, then it seems the problem is somewhere else.

[COLOR=DarkRed]Go to System -> Admin -> Synaptic Package Manager, then select Settings -> Repositories. What do you have under "Other Software". One of those is probably blocking the updates, you should uncheck the wrong one.[/COLOR] That fixed the issue thank you.=D>

---

### Post by 3Miro on 2011-03-30
> **BluDawg said:**
> That fixed the issue thank you.=D>

If you have no more questions, then please mark the thread as "solved".

---

