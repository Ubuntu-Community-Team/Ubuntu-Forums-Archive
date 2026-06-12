---
title: "Corrupted repositories?"
date: 2010-07-20
forum: General Help
---

### Post by windowm on 2010-07-20
I'm fairly new to linux and recently tried adding Medibuntu to my repositories, but I may have added an outdated repository. In the process of trying to fix the problem and revert to an error-free state I may have made the problem worse :/ . I am using Ubuntu 10.04 LTS.

Here is the message I get from Synaptic Package Manager:
```
Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages)Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_i18n_Translation-en%5fCA)Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

The sources.list file from /etc/apt/ :
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid partner main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse partner
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ca.archive.ubuntu.com/ubuntu/ lucid-security main restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid partner
deb http://security.ubuntu.com/ubuntu/ lucid-security partner restricted main multiverse universe
deb http://ca.archive.ubuntu.com/ubuntu/ lucid restricted
```

The terminal output I get from
 sudo apt-get update
```
max@max-satellite:/etc/apt$ sudo apt-get update
Hit http://ca.archive.ubuntu.com lucid Release.gpg
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/partner Translation-en_CA
Get:1 http://ca.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA 
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/partner Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com lucid-backports Release.gpg         
Hit http://archive.canonical.com lucid Release                       
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com lucid-security Release.gpg
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Hit http://archive.canonical.com lucid/partner Packages              
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/partner Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com lucid Release 
Hit http://archive.canonical.com lucid/partner Sources                                     
Get:2 http://ca.archive.ubuntu.com lucid-updates Release [44.7kB]    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_CA
Hit http://security.ubuntu.com lucid-security Release
Hit http://ca.archive.ubuntu.com lucid-backports Release
Hit http://ca.archive.ubuntu.com lucid-security Release
Hit http://ca.archive.ubuntu.com lucid/main Sources
Hit http://ca.archive.ubuntu.com lucid/restricted Sources
Hit http://ca.archive.ubuntu.com lucid/main Packages
Hit http://ca.archive.ubuntu.com lucid/restricted Packages
Hit http://ca.archive.ubuntu.com lucid/multiverse Packages
Get:3 http://ca.archive.ubuntu.com lucid-updates/restricted Packages [3,252B]
Get:4 http://ca.archive.ubuntu.com lucid-updates/main Packages [264kB]
Get:5 http://ca.archive.ubuntu.com lucid-updates/multiverse Packages [3,771B]
Hit http://ca.archive.ubuntu.com lucid-backports/main Packages
Hit http://ca.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://ca.archive.ubuntu.com lucid-backports/universe Packages
Hit http://ca.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://ca.archive.ubuntu.com lucid-backports/main Sources
Hit http://ca.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://ca.archive.ubuntu.com lucid-backports/universe Sources
Hit http://ca.archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com lucid-security/main Packages
Hit http://ca.archive.ubuntu.com lucid-security/restricted Packages
Hit http://ca.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://ca.archive.ubuntu.com lucid-security/restricted Sources
Hit http://ca.archive.ubuntu.com lucid-security/main Sources
Hit http://ca.archive.ubuntu.com lucid-security/multiverse Sources
Hit http://ca.archive.ubuntu.com lucid-security/universe Sources
Hit http://ca.archive.ubuntu.com lucid-security/universe Packages
Fetched 316kB in 2s (109kB/s)
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/Release  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm really hoping I don't have to reinstall Ubuntu because of this. If as a last resort, is it possible to revert the repositories to installation defaults? Thanks for taking the time to read, hopefully this problem can be solved ;)

---

### Post by warfacegod on 2010-07-20
Go to: System> Admin.> Software Sources> Authentication tab> bottom right click "Restore Defaults".

---

### Post by windowm on 2010-07-20
I just tried that and I'm still getting an error. Synaptic Package Manager came up with this:
```
W: Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_i18n_Translation-en%5fCA)
```

also apt-get update still gives me the same type errors

---

### Post by giddyup306 on 2010-07-20
> **windowm said:**
> I just tried that and I'm still getting an error. Synaptic Package Manager came up with this:
```
W: Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_lucid_restricted_i18n_Translation-en%5fCA)
```also apt-get update still gives me the same type errors

I'm having the same problems as you.  

[http://ubuntuforums.org/showthread.php?t=1534716](http://ubuntuforums.org/showthread.php?t=1534716)

---

### Post by windowm on 2010-07-20
I created a backup and deleted the existing sources.list file. After opening Software Sources and changing a few settings it simply created a new sources.list file. For now it seems my problem is solved XD

---

