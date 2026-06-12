---
title: "Requires installation of untrusted packages"
date: 2010-12-23
forum: General Help
---

### Post by MrLeprechawn on 2010-12-23
Ubuntu 10.10
Error while trying to update in Update Manager
I have seen this error in other threads and as suggested I went into Synaptic Update Manager and changed the repositories. Turned off Software restricted by copyright or legal issues (multiverse) and I also ticked Canonical Partners in other software. I then reloaded the manager and got another error.
```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```These are the details
```
Failed to fetch http://ie.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'ie.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas?

---

### Post by sikander3786 on 2010-12-23
Software Center > Edit > Software Sources > Change download server to 'Main'.

Then from Applications > Accessories > Terminal, post the _complete_ output of this command.

```
sudo apt-get update
```

---

### Post by karthick87 on 2010-12-23
Post the output of,
```
cat /etc/apt/sources.list
```
```
ls -l /etc/apt/sources.list.d
```

---

### Post by MrLeprechawn on 2010-12-23
> **sikander3786 said:**
> Software Center > Edit > Software Sources > Change download server to 'Main'.

Then from Applications > Accessories > Terminal, post the _complete_ output of this command.

```
sudo apt-get update
```


When I enter 
```
sudo apt-get update
```
It asks for my password but it wont let me enter it. I type but nothing happens. Sorry for these newbie questions.
One extra question, how do you remove the need to authenticate all the time?

---

### Post by sikander3786 on 2010-12-23
> It asks for my password but it wont let me enter it. I type but nothing happens.

It won't return any asterisks or characters when you type it. Just type blindly and hit Enter ;-)

The other question regarding authentication, later....

---

### Post by MrLeprechawn on 2010-12-23
```
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IE       
Hit http://extras.ubuntu.com maverick Release                                  
Hit http://extras.ubuntu.com maverick/main Sources                             
Hit http://extras.ubuntu.com maverick/main i386 Packages                    
Hit http://archive.ubuntu.com maverick Release.gpg                          
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_IE
Hit http://archive.ubuntu.com maverick-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_IE
Hit http://archive.ubuntu.com maverick-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_IE
Hit http://archive.ubuntu.com maverick Release
Hit http://archive.ubuntu.com maverick-updates Release                         
Hit http://archive.ubuntu.com maverick-security Release                        
Hit http://archive.ubuntu.com maverick/main Sources            
Hit http://archive.ubuntu.com maverick/restricted Sources      
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Err http://archive.canonical.com maverick Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_IE
Hit http://archive.canonical.com maverick Release
Ign http://archive.canonical.com maverick/partner Sources/DiffIndex
Ign http://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Hit http://archive.canonical.com maverick/partner Sources
Hit http://archive.canonical.com maverick/partner i386 Packages
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sikander3786 on 2010-12-23
> W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

No definite clues on that one.

Sometimes it happens due to DNS problems where your router is acting as a DNS server at the same time and is unable to resolve the host names.

Try using Google DNS and let us know how that goes. See Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

### Post by MrLeprechawn on 2010-12-23
> **karthick87 said:**
> Post the output of,
```
cat /etc/apt/sources.list
``````
ls -l /etc/apt/sources.list.d
```

First one
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

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
# deb http://ie.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security restricted main universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu maverick-security universe
```

Second
```
total 0
```

---

