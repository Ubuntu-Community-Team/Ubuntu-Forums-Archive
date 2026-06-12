---
title: "Can't update to the latest Kernel"
date: 2010-01-02
forum: General Help
---

### Post by macstr1k3r on 2010-01-02
Hey. I juset reinstalled my ubuntu and i can't update to the latest kernel. I'm stuck at 2.6.31-15. Also my grub is v1.94 Beta4 and can't upgrade it to grub2. Help please.

---

### Post by starcraft.man on 2010-01-02
> **macstr1k3r said:**
> Hey. I juset reinstalled my ubuntu and i can't update to the latest kernel. I'm stuck at 2.6.31-15. Also my grub is v1.94 Beta4 and can't upgrade it to grub2. Help please.

hmmm? Why are you stuck?

At a terminal can you do the following. Terminal at Applications > Accessories > Terminal (follow prompts):

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by macstr1k3r on 2010-01-02
```
sudo apt-get update && sudo apt-get dist-upgrade
```and I get
```
Hit http://ubuntu.etf.bg.ac.rs karmic Release.gpg
Ign http://ubuntu.etf.bg.ac.rs karmic/main Translation-en_US                  
Ign http://ubuntu.etf.bg.ac.rs karmic/restricted Translation-en_US            
Ign http://ubuntu.etf.bg.ac.rs karmic/universe Translation-en_US              
Ign http://ubuntu.etf.bg.ac.rs karmic/multiverse Translation-en_US
Hit http://ubuntu.etf.bg.ac.rs karmic-updates Release.gpg
Ign http://ubuntu.etf.bg.ac.rs karmic-updates/main Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-updates/restricted Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-updates/universe Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-updates/multiverse Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US
Hit http://ubuntu.etf.bg.ac.rs karmic-security Release.gpg
Hit http://archive.canonical.com karmic Release                            
Ign http://ubuntu.etf.bg.ac.rs karmic-security/main Translation-en_US      
Ign http://ubuntu.etf.bg.ac.rs karmic-security/restricted Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-security/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages
Ign http://ubuntu.etf.bg.ac.rs karmic-security/multiverse Translation-en_US
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed Release.gpg
Ign http://ubuntu.etf.bg.ac.rs karmic-proposed/restricted Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-proposed/main Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-proposed/multiverse Translation-en_US
Ign http://ubuntu.etf.bg.ac.rs karmic-proposed/universe Translation-en_US
Hit http://ubuntu.etf.bg.ac.rs karmic Release
Hit http://ubuntu.etf.bg.ac.rs karmic-updates Release                     
Hit http://ubuntu.etf.bg.ac.rs karmic-security Release
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed Release
Hit http://ubuntu.etf.bg.ac.rs karmic/main Packages
Hit http://ubuntu.etf.bg.ac.rs karmic/restricted Packages
Hit http://ubuntu.etf.bg.ac.rs karmic/main Sources
Hit http://ubuntu.etf.bg.ac.rs karmic/restricted Sources
Hit http://ubuntu.etf.bg.ac.rs karmic/universe Packages
Hit http://ubuntu.etf.bg.ac.rs karmic/universe Sources
Hit http://ubuntu.etf.bg.ac.rs karmic/multiverse Packages
Hit http://ubuntu.etf.bg.ac.rs karmic/multiverse Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/main Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/restricted Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/main Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/restricted Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/universe Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/universe Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/multiverse Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-updates/multiverse Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-security/main Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-security/restricted Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-security/main Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-security/restricted Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-security/universe Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-security/universe Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-security/multiverse Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-security/multiverse Sources
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed/restricted Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed/main Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed/multiverse Packages
Hit http://ubuntu.etf.bg.ac.rs karmic-proposed/universe Packages
Reading package lists... Done                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I don't see any newer linux-image in the synpatic, and the update manager is empty!

---

### Post by Leppie on 2010-01-02
check your sources.list, go to Sysem>Administration>Software Sources, go to the updates tab and make sure that at least the first two options are ticked. then run apt-get update and apt-get dist-upgrade again, or check with update manager.

---

### Post by warfacegod on 2010-01-02
> I don't see any newer linux-image in the synpatic, and the update manager is empty!

I posted about this over in the security section. Me and another user are having the same issue.

[http://ubuntuforums.org/showthread.php?t=1370343]("http://ubuntuforums.org/showthread.php?t=1370343")

I'm posting the link in case we find a solution.

---

### Post by macstr1k3r on 2010-01-02
> **Leppie said:**
> check your sources.list, go to Sysem>Administration>Software Sources, go to the updates tab and make sure that at least the first two options are ticked. then run apt-get update and apt-get dist-upgrade again, or check with update manager.

My software sources are fine, the first thing I checked!

---

### Post by starcraft.man on 2010-01-02
> **macstr1k3r said:**
> My software sources are fine, the first thing I checked!

Can you try a different server please? Maybe it's having trouble/not updated. Can be changed in the software sources pane, iWeb works well out in Canada.

---

### Post by Leppie on 2010-01-02
> **macstr1k3r said:**
> My software sources are fine, the first thing I checked!

i'm sorry i didn't get that straight away from your post...
you might want to elaborate on the troubleshooting you've done before coming to a forum when posting...

---

