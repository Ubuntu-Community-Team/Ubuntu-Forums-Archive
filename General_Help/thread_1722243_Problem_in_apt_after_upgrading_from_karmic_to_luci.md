---
title: "Problem in apt after upgrading from karmic to lucid..."
date: 2011-04-05
forum: General Help
---

### Post by NamanShekharMishra on 2011-04-05
After I upgrading from Karmic to Lucid, I haven't been able to update my version further and also running apt-get shows error... Can anyone tell me why this is happening?
The error is: 
```

#sudo apt-get update
Err http://archive.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

``` and some more lines showing the same error.Please tell me how to correct it...

---

### Post by zvacet on 2011-04-05
In terminal

```
cat /etc/apt/sources.list
```

and post output here.

---

### Post by NamanShekharMishra on 2011-04-06
> **zvacet said:**
> In terminal

```
cat /etc/apt/sources.list
```and post output here.


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) lucid free non-free # disabled on upgrade to lucid

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) lucid main

---

### Post by matt_symes on 2011-04-06
Hi

A couple of people have had this issue on the forums. 

Apart from the references to Karmic i could not see much wrong with the structure.

So lets try this.

Open a terminal and type..

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
```

Enter your password. It will not be echoed to the screen. This is normal. It will backup your existing sources.list file. then type

```
sudo nano /etc/apt/sources.list
```

Copy and paste the text below into nano using the mouse and right clicking.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu lucid universe
deb http://in.archive.ubuntu.com/ubuntu lucid-updates universe
deb http://medibuntu.sos-sts.com/repo/ lucid free non-free # disabled on upgrade to lucid

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu lucid multiverse
deb http://in.archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
#deb-src http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://in.archive.canonical.com/ubuntu lucid partner
deb-src http://in.archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://in.archive.ubuntu.com/ubuntu lucid-security universe
deb http://in.archive.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/fta/ubuntu lucid main
```

Press Ctrl + o to save and Ctrl + x to exit. Then type..

```
sudo apt-get update
```

Post back any errors.

Kind regards

---

### Post by NamanShekharMishra on 2011-04-07
> **matt_symes said:**
> Hi

A couple of people have had this issue on the forums. 

Apart from the references to Karmic i could not see much wrong with the structure.

So lets try this.

Open a terminal and type..

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
```Enter your password. It will not be echoed to the screen. This is normal. It will backup your existing sources.list file. then type

```
sudo nano /etc/apt/sources.list
```Copy and paste the text below into nano using the mouse and right clicking.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu lucid universe
deb http://in.archive.ubuntu.com/ubuntu lucid-updates universe
deb http://medibuntu.sos-sts.com/repo/ lucid free non-free # disabled on upgrade to lucid

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu lucid multiverse
deb http://in.archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
#deb-src http://in.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://in.archive.canonical.com/ubuntu lucid partner
deb-src http://in.archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://in.archive.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://in.archive.ubuntu.com/ubuntu lucid-security universe
deb http://in.archive.ubuntu.com/ubuntu lucid-security multiverse
deb http://ppa.launchpad.net/fta/ubuntu lucid main
```Press Ctrl + o to save and Ctrl + x to exit. Then type..

```
sudo apt-get update
```Post back any errors.

Kind regards

Did what you mentioned. Doesn't work.
```
Err http://in.archive.canonical.com lucid Release.gpg
  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid Release.gpg                                 
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net/fta/ubuntu/ lucid/main Translation-en_IN          
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid Release.gpg                             
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://in.archive.canonical.com/ubuntu/ lucid/partner Translation-en_IN    
  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com/repo/ lucid/free Translation-en_IN            
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net lucid Release
Err http://medibuntu.sos-sts.com/repo/ lucid/non-free Translation-en_IN    
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Ign http://in.archive.canonical.com lucid Release                          
Err http://archive.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://medibuntu.sos-sts.com lucid Release
Ign http://in.archive.canonical.com lucid/partner Packages
Ign http://archive.ubuntu.com lucid-security Release
Ign http://medibuntu.sos-sts.com lucid/free Packages
Ign http://in.archive.canonical.com lucid/partner Sources
Ign http://archive.ubuntu.com lucid-security/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://archive.ubuntu.com lucid-security/restricted Packages
Err http://ppa.launchpad.net lucid/main Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://in.archive.canonical.com lucid/partner Packages                     
Ign http://archive.ubuntu.com lucid-security/main Packages                     
Ign http://medibuntu.sos-sts.com lucid/non-free Packages                       
Ign http://medibuntu.sos-sts.com lucid/free Packages                           
Ign http://in.archive.canonical.com lucid/partner Sources
Ign http://medibuntu.sos-sts.com lucid/non-free Packages
Err http://in.archive.canonical.com lucid/partner Packages
  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com lucid-security/restricted Packages
Err http://medibuntu.sos-sts.com lucid/free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://in.archive.canonical.com lucid/partner Sources
  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-security/main Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://medibuntu.sos-sts.com lucid/non-free Packages
  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com lucid-security/restricted Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid Release.gpg
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates Release.gpg
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security Release.gpg
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://in.archive.ubuntu.com lucid Release
Ign http://in.archive.ubuntu.com lucid-updates Release
Ign http://in.archive.ubuntu.com lucid-security Release
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid/universe Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-security/restricted Sources
Ign http://in.archive.ubuntu.com lucid-security/main Sources
Ign http://in.archive.ubuntu.com lucid-security/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-security/universe Sources
Ign http://in.archive.ubuntu.com lucid-security/universe Packages
Ign http://in.archive.ubuntu.com lucid-security/multiverse Packages
Ign http://in.archive.ubuntu.com lucid/main Packages
Ign http://in.archive.ubuntu.com lucid/restricted Packages
Ign http://in.archive.ubuntu.com lucid/restricted Sources
Ign http://in.archive.ubuntu.com lucid/main Sources
Ign http://in.archive.ubuntu.com lucid/multiverse Sources
Ign http://in.archive.ubuntu.com lucid/universe Sources
Ign http://in.archive.ubuntu.com lucid/universe Packages
Ign http://in.archive.ubuntu.com lucid/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-updates/main Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://in.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://in.archive.ubuntu.com lucid-updates/main Sources
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Sources
Ign http://in.archive.ubuntu.com lucid-updates/universe Packages
Ign http://in.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://in.archive.ubuntu.com lucid-security/restricted Sources
Ign http://in.archive.ubuntu.com lucid-security/main Sources
Ign http://in.archive.ubuntu.com lucid-security/multiverse Sources
Ign http://in.archive.ubuntu.com lucid-security/universe Sources
Ign http://in.archive.ubuntu.com lucid-security/universe Packages
Ign http://in.archive.ubuntu.com lucid-security/multiverse Packages
Err http://in.archive.ubuntu.com lucid/main Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/restricted Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/universe Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid/multiverse Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/main Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/restricted Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/universe Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-updates/multiverse Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/universe Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com lucid-security/multiverse Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/Release.gpg  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/fta/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/fta/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/fta/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz  Something wicked happened resolving 'in.archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/lucid/non-free/binary-i386/Packages.gz  Something wicked happened resolving 'medibuntu.sos-sts.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by NamanShekharMishra on 2011-04-07
I forgot to mention that my machine is behind a http proxy

---

### Post by matt_symes on 2011-04-08
Hi

The first thing i would do is rollback to the saved sources file.
[FONT=monospace]
[/FONT]```
sudo rm /etc/apt/sources.list
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
```

> **NamanShekharMishra said:**
> I forgot to mention that my machine is behind a http proxy

This could be important. Have you configured your proxy settings ?

System->Preferences->Network proxy (or somesuch in lucid)

Kind regards

---

