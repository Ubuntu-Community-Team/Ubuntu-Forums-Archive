---
title: "Update download not functional (that little red tringle in the menu bar)"
date: 2010-10-17
forum: General Help
---

### Post by b9k9kiwi on 2010-10-17
I am getting a red triangle with exclamation mark 'warning' in the menu bar (relating to update repositories) which has been reported but no 'fixes' seem to work for me.

When I click on the triangle and then click on 'check' in the Update Manager all proceeds normally without any error messages - then concludes by telling me that there are no updates to install.

I can't believe that there have been no updates for 11 days.

Any advice or help appreciated.

Ubuntu 10.10
Fresh Install

---

### Post by sikander3786 on 2010-10-17
It often appears when the repository information is outdated. Did you disable any repositories?

Please post the output of

```
sudo apt-get update
```

---

### Post by b9k9kiwi on 2010-10-17
> **sikander3786 said:**
> 
...
Please post the output of

```
sudo apt-get update
```

Code:
tony@MusicMachine:~$ sudo apt-get update
[sudo] password for tony: 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick Release.gpg
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en 
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security Release.gpg
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick Release                         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates Release                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security Release                
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/main Sources                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/restricted Sources         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/main Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/multiverse Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/main i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) maverick-security/multiverse i386 Packages
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_NZ
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release
  
Fetched 66B in 1s (55B/s)  
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
tony@MusicMachine:~$

---

### Post by sikander3786 on 2010-10-17
And,

```
cat /etc/apt/sources.list
```

---

### Post by b9k9kiwi on 2010-10-17
> **sikander3786 said:**
> And,

```
cat /etc/apt/sources.list
```

Output:

tony@MusicMachine:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release Candidate i386 (20100928)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security main restricted
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) maverick-security multiverse
tony@MusicMachine:~$

---

### Post by robert shearer on 2010-10-17
the code in the last post for the following thread fixed it for me...
[http://ubuntuforums.org/showthread.php?t=1589807](http://ubuntuforums.org/showthread.php?t=1589807)

The key indicator is in your output....
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192 W: Failed to fetch ...

I had the same one and googled it to find the link above.

---

### Post by b9k9kiwi on 2010-10-22
> **robert shearer said:**
> the code in the last post for the following thread fixed it for me...
[http://ubuntuforums.org/showthread.php?t=1589807](http://ubuntuforums.org/showthread.php?t=1589807)

The key indicator is in your output....
.

I had the same one and googled it to find the link above.


Thank you - that fixed it.

---

