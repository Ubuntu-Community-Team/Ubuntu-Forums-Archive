---
title: "No KDE updates Karmic  (9.10)"
date: 2010-01-02
forum: General Help
---

### Post by OldAlgis on 2010-01-02
Hi,

I installed Karmic kubutu from a DVD.  Great desktop, graphics lovely, but broken update system. It tells me that there are over 130 security updates and fails to install any one... As new GRUB on karmic kubuntu is beta2 and,  more significantly, KDE 4.x is beta1, it is not going to improve by itself, is it?

There must be a few simple commands to install the upgrades, but what are they?

I am happy to use CLI.  Any and all CLI 'cooking receipes' for upgrades or re-installation will be greatly appreciated.

---

### Post by MelDJ on 2010-01-02
what error comes up if you try updating?

---

### Post by OldAlgis on 2010-01-02
> **MelDJ said:**
> what error comes up if you try updating?

@MelDJ It just falls over quietly.  Very, very quietly. From what I can gather from others trying KDE 4.3, it is still buggy.

Thanks for talking to me!

---

### Post by MelDJ on 2010-01-02
hey..no problem...
type sudo apt-get update in terminal and post the output here

---

### Post by OldAlgis on 2010-01-02
> **MelDJ said:**
> 
type sudo apt-get update in terminal and post the output here
ak@amd64:~$ sudo apt-get update
[sudo] password for ak:        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic Release.gpg         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Translation-en_AU                                
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Translation-en_AU                          
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Translation-en_AU                            
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multivese Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Reading package lists... Done
ak@amd64:~$

I am in the dark...  And talking to MelDJ from kubuntu 9.10. Has not frozen up yet.  It just told me that there are 135 security updates in a pop-up window.

Thanks Mel, but where do I go from here?

---

