---
title: "Errors after running sudo apt-get update"
date: 2011-12-20
forum: General Help
---

### Post by Maleificus on 2011-12-20
After running sudo apt-get update I am getting these errors at the end of the output.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu/) oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_kubuntu-ppa_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)

---

### Post by oldos2er on 2011-12-20
For the NO_PUBKEY error, ```
run sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` where KEYID is number shown in error msg.

Can you post the output of ```
ls /etc/apt/sources.list.d/
``` ?

---

### Post by Maleificus on 2011-12-21
richard@Kelsie:~$ ls /etc/apt/sources.list.d/
banshee-team-ppa-oneiric.list                  oneiric-partner.list~
banshee-team-ppa-oneiric.list~                 oneiric-partner.list.save
banshee-team-ppa-oneiric.list.save             oneiric-partner.list.save~
banshee-team-ppa-oneiric.list.save~            playdeb.list
me-davidsansome-clementine-oneiric.list        psyke83-ppa-oneiric.list
me-davidsansome-clementine-oneiric.list~       psyke83-ppa-oneiric.list~
me-davidsansome-clementine-oneiric.list.save   psyke83-ppa-oneiric.list.save
me-davidsansome-clementine-oneiric.list.save~  psyke83-ppa-oneiric.list.save~
oneiric-partner.list

---

### Post by oldos2er on 2011-12-21
Can we see your sources.list too? ```
cat /etc/apt/sources.list
```

---

### Post by Maleificus on 2011-12-21
richard@Kelsie:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/restricted/binary-i386/
# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

