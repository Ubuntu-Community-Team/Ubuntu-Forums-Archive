---
title: "i cant update and install programs"
date: 2010-09-29
forum: General Help
---

### Post by i6q on 2010-09-29
hi

when i update my Ubuntu it gaive my


W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


what i do can any one help sorry im now user

---

### Post by andrewthomas on 2010-09-29
post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2010-09-29
Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is number shown in error msg.

---

### Post by i6q on 2010-09-29
> **oldos2er said:**
> Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is number shown in error msg.

it ok 
There were 6 problems and now 3 problems 
 can i get solution to them

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


  :(

---

### Post by 7h3d4rk0n3 on 2010-09-29
Try doing:
```
sudo apt-get update
```

---

### Post by i6q on 2010-09-29
> **7h3d4rk0n3 said:**
> Try doing:
```
sudo apt-get update
```

it same 

> x-man@x-man-desktop:~$ sudo apt-get update
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]                           
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_US          
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,310B]                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic/partner Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Get:3 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release.gpg
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources                      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [14B]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Fetched 2,668B in 10s (257B/s)                                                 
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
x-man@x-man-desktop:~$ 


---

### Post by 7h3d4rk0n3 on 2010-09-29
If you go to "System >> Administration >> Software Sources" what do you have checked under your "Ubuntu Software" tab.

---

### Post by barney385 on 2010-09-29
> **oldos2er said:**
> Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is number shown in error msg.

Thank you, been trying to fix this through different means for days.

Ugh, finally.

:)

---

### Post by i6q on 2010-09-29
> **7h3d4rk0n3 said:**
> If you go to "System >> Administration >> Software Sources" what do you have checked under your "Ubuntu Software" tab.

[IMG]http://files03.arb-up.com/i/00278/7byb62gdzy1s.png[/IMG]


[IMG]http://files03.arb-up.com/i/00278/a1f5ljg6tk1m.png[/IMG]

---

### Post by 7h3d4rk0n3 on 2010-09-29
Good to here, make sure you mark this as [SOLVED].

---

### Post by i6q on 2010-09-29
> **7h3d4rk0n3 said:**
> Good to here, make sure you mark this as [SOLVED].


Thank you, You have helped me a lot

I hope to find a solution to the problem

---

### Post by i6q on 2010-09-30
> **i6q said:**
> it ok 
There were 6 problems and now 3 problems 
 can i get solution to them

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


  :(


any one help plzzzzzzzz

---

### Post by oldos2er on 2010-09-30
Not sure why you're getting the warning "W: Failed to fetch http://archive.ubuntu.com/ubuntu/dis...pdates/Release", it's working here. Have you tried different servers?

Also try ```
sudo apt-key update
```

---

