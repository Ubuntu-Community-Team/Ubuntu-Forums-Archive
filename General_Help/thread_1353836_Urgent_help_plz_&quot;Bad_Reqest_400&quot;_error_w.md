---
title: "Urgent help plz: &quot;Bad Reqest 400&quot; error wont let the system update or install"
date: 2009-12-13
forum: General Help
---

### Post by emigrant on 2009-12-13
hi all,
i cannot update or install anything on the system as i get this error: bad request 400
i can access the internet through firefox; either through tor or without tor.

here is the sourcelist:

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

#tor
deb http://deb.torproject.org/torproject.org jaunty main

# Remastersys
deb http://www.geekconnection.org/remastersys/repository ubuntu/
```


thank you very much for your help

---

### Post by emigrant on 2009-12-13
bump :popcorn:

---

### Post by dcstar on 2009-12-14
> **emigrant said:**
> hi all,
i cannot update or install anything on the system as i get this error: bad request 400
.........
thank you very much for your help

Unless you tell us the** whole** error, nothing can be done.

---

### Post by emigrant on 2009-12-14
> **dcstar said:**
> Unless you tell us the** whole** error, nothing can be done.
yes sure here it is with additional info: :)

```
$ ls -l /etc/apt/sources.list*
-rw-r--r-- 1 root root 3085 2009-12-13 19:12 /etc/apt/sources.list
-rw-r--r-- 1 root root 3084 2009-12-13 18:43 /etc/apt/sources.list~
-rw-r--r-- 1 root root 3120 2009-12-13 18:43 /etc/apt/sources.list.save

/etc/apt/sources.list.d:
total 0
emigrant@emigrant-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

#tor
#deb http://deb.torproject.org/torproject.org jaunty main

# Remastersys
deb http://www.geekconnection.org/remastersys/repository ubuntu/


emigrant@emigrant-desktop:~$ sudo apt-get update
Ign http://www.geekconnection.org ubuntu/ Release.gpg
Ign http://archive.ubuntu.com jaunty Release.gpg                      
Ign http://www.geekconnection.org ubuntu/ Translation-en_US                    
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Release                              
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Packages                             
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Packages                             
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Err http://www.geekconnection.org ubuntu/ Packages                             
  400 Bad Request
Ign http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty Release     
Ign http://archive.ubuntu.com jaunty-updates Release
Ign http://archive.ubuntu.com jaunty-security Release
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://archive.ubuntu.com jaunty/main Packages
Ign http://archive.ubuntu.com jaunty/restricted Packages
Ign http://archive.ubuntu.com jaunty/main Sources
Ign http://archive.ubuntu.com jaunty/restricted Sources
Ign http://archive.ubuntu.com jaunty/universe Packages
Ign http://archive.ubuntu.com jaunty/universe Sources
Ign http://archive.ubuntu.com jaunty/multiverse Packages
Ign http://archive.ubuntu.com jaunty/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates/main Packages
Ign http://archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://archive.ubuntu.com jaunty-updates/universe Packages
Ign http://archive.ubuntu.com jaunty-updates/universe Sources
Ign http://archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-security/main Packages
Ign http://archive.ubuntu.com jaunty-security/restricted Packages
Ign http://archive.ubuntu.com jaunty-security/main Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Sources
Ign http://archive.ubuntu.com jaunty-security/universe Packages
Ign http://archive.ubuntu.com jaunty-security/universe Sources
Ign http://archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://archive.ubuntu.com jaunty-security/multiverse Sources
Err http://archive.ubuntu.com jaunty/main Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty/restricted Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty/main Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty/restricted Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty/universe Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty/universe Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty/multiverse Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty/multiverse Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/main Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/restricted Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/main Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/restricted Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/universe Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/universe Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/multiverse Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-updates/multiverse Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/main Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/restricted Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/main Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/restricted Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/universe Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/universe Sources
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/multiverse Packages
  400 Bad Request
Err http://archive.ubuntu.com jaunty-security/multiverse Sources
  400 Bad Request
W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  400 Bad RequestE: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by emigrant on 2009-12-15
bump :popcorn:

---

### Post by dcstar on 2009-12-15
> **emigrant said:**
> yes sure here it is with additional info: :)

```
$ ls -l /etc/apt/sources.list*
-rw-r--r-- 1 root root 3085 2009-12-13 19:12 /etc/apt/sources.list
-rw-r--r-- 1 root root 3084 2009-12-13 18:43 /etc/apt/sources.list~
-rw-r--r-- 1 root root 3120 2009-12-13 18:43 /etc/apt/sources.list.save

/etc/apt/sources.list.d:
total 0
emigrant@emigrant-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://lk.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

#tor
#deb http://deb.torproject.org/torproject.org jaunty main

# Remastersys
**deb http://www.geekconnection.org/remastersys/repository ubuntu/**


emigrant@emigrant-desktop:~$ sudo apt-get update
Ign http://www.geekconnection.org ubuntu/ Release.gpg
Ign http://archive.ubuntu.com jaunty Release.gpg                      
Ign http://www.geekconnection.org ubuntu/ Translation-en_US                    
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Release                              
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Packages                             
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://www.geekconnection.org ubuntu/ Packages                             
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
[B]Err http://www.geekconnection.org ubuntu/ Packages                             
  400 Bad Request[/B]
Ign http://archive.ubuntu.com jaunty-updates Release.gpg
......
```

Since the first error occurs at this repository, I suggest you remove it and try again.

Do you notice the obvious difference in that entry compared to every single other entry?

---

### Post by emigrant on 2009-12-15
hi,
now i get a different error:
(@ dcstar didn't remove the repo yet)

```
$ sudo apt-get update
Err http://www.geekconnection.org ubuntu/ Release.gpg
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty Release.gpg                               
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://www.geekconnection.org ubuntu/ Translation-en_US                    
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty/main Translation-en_US                    
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty/restricted Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty/universe Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty/multiverse Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-updates Release.gpg
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-updates/main Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-security Release.gpg
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-security/main Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-security/universe Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Err http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)
Reading package lists... Done                   
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/Release.gpg  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Failed to fetch http://www.geekconnection.org/remastersys/repository/ubuntu/en_US.bz2  Could not connect to 79.174.64.146:8000 (79.174.64.146). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

---

### Post by emigrant on 2009-12-15
is it because of TOR im using? :confused:

---

### Post by emigrant on 2009-12-15
hi dcstar,
i commented out that, and still get the error as in post #7 :(

---

### Post by emigrant on 2009-12-15
each time i get a different error:

```
Ign http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security Release.gpg
Ign http://us.archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty Release  
Ign http://us.archive.ubuntu.com jaunty-updates Release
Ign http://us.archive.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-security/main Sources
Ign http://us.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-security/universe Packages
Ign http://us.archive.ubuntu.com jaunty-security/universe Sources
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-security/main Sources
Ign http://us.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-security/universe Packages
Ign http://us.archive.ubuntu.com jaunty-security/universe Sources
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Sources
Err http://us.archive.ubuntu.com jaunty/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty/multiverse Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/main Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/restricted Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/main Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/restricted Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/universe Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/universe Sources
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/multiverse Packages
  400 Bad Request
Err http://us.archive.ubuntu.com jaunty-security/multiverse Sources
  400 Bad Request
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  400 Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  400 Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by emigrant on 2009-12-17
double bump :popcorn:

---

### Post by emigrant on 2009-12-19
i completely removed TOR and polipo but the problem still persists... :(
can any one give me an original jauny source.list please?
thank you very much.

---

