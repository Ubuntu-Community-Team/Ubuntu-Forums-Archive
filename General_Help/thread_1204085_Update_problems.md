---
title: "Update problems"
date: 2009-07-04
forum: General Help
---

### Post by axxjaj on 2009-07-04
Hello
I am having a problem with my update manager, which will not update. I post below the reults and "Orange No 3" is the name of my WIFI connection. BTW I am running Hardy heron. Any help gratefully received.


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.4.1-1ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.4.1-1ubuntu2.1_all.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.4.1-1ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.4.1-1ubuntu2.1_all.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.4.1-1ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.4.1-1ubuntu2.1_all.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_2.4.1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_2.4.1-1ubuntu2.1_i386.deb)
  Could not resolve ‘Orange No 3’

---

### Post by axxjaj on 2009-07-04
Hello _ post below the output for cat /etc/apt/sources.list


andrew@andrew-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
andrew@andrew-laptop:~$ sudo apt-get update
[sudo] password for andrew: 
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
  Could not resolve ‘Orange No 3’
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg        
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
  Could not resolve ‘Orange No 3’
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
  Could not resolve ‘Orange No 3’
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2](http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2)  Could not resolve ‘Orange No 3’

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by PmDematagoda on 2009-07-04
Can you access the internet properly over the WiFi connection?

---

### Post by axxjaj on 2009-07-04
Hi - the WIFI is working pefectly. I hope you can help.

---

