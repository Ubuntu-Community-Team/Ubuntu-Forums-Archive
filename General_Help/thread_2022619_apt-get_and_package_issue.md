---
title: "apt-get and package issue"
date: 2012-07-11
forum: General Help
---

### Post by zzdjchris on 2012-07-11
I currently have a big red dot with a white line through it, and it came about while trying to get my Brother MFC-640CW working (which still isn't).
  But now this Big Red Dot is my new problem, as it's preventing me from using "Synaptic Package Manager". I think it's having trouble getting exclusive access because of my "Big Red DOT"!
  So, I went through "Terminal" trying to fix it, and this is what I got, and also as far as I can get (and STILL with a 'BIG RED DOT')

  (mfc210clpr is the Package I now need to remove to move forward).

zzdjchris@WebX-dEsign-Server:~$ apt-get remove mfc210clpr
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
zzdjchris@WebX-dEsign-Server:~$ sudo apt-get remove mfc210clpr
[sudo] password for zzdjchris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc210clpr needs to be reinstalled, but I can't find an archive for it.
zzdjchris@WebX-dEsign-Server:~$ sudo apt-get purge mfc210clpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc210clpr needs to be reinstalled, but I can't find an archive for it.
zzdjchris@WebX-dEsign-Server:~$

  Any ideas?

  Thanks in advance.

---

### Post by raja.genupula on 2012-07-11
post the output of ```
dpkg -s mfc210clpr
```

---

### Post by zzdjchris on 2012-07-13
Sorry for the late reply

here it is...

```

zzdjchris@WebX-dEsign-Server:~$ dpkg -s mfc210clpr
Package: mfc210clpr
Status: deinstall reinstreq half-installed
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.0.2-1
Config-Version: 1.0.2-1
Description: Brother lpr Inkjet Printer Definitions
 Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
 Brother inkjet printer Driver
zzdjchris@WebX-dEsign-Server:~$ 

```Thanks.

---

### Post by jmfal on 2012-07-13
Welcome to Ubuntu
Run this in a terminal
```
  sudo rm /var/lib/dpkg/lock   
```

And then
```
  sudo apt-get install -f    
```

Then
```
  sudo apt-get clean
               sudo apt-get autoclean     
                sudo apt-get autoremove  
```

---

