---
title: "Network manager gone - can't connect"
date: 2010-10-05
forum: General Help
---

### Post by FeyerbrandX on 2010-10-05
This has happened a few months ago, but just haven't gotten around to fixing it yet.  But with 10.10 coming up soon, I would like to get it fixed so it can update.

I am currently using my Vista partition, which can connect to the network just fine.  But ubuntu, no matter what (unplug/replug router, modem, router&modem, etc) will not connect.

Is there a way to reinstall network manager from a CD or SD card?  Whenever I try to sudo ap get it, it will error out since it can't pull it from the default (internet) source.

---

### Post by spiky001 on 2010-10-05
if you have the original cd open software sources tick the bit down the bottom about cd then when you use package manager it will look for the cd (which is in the drive)

---

### Post by FeyerbrandX on 2010-10-10
I burned a 10.04 disc, but it wouldn't connect.

I also tried to use a new 10.10 disc, but the same problem.

This is what happens about 3/5ths through the status bar:

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com' 

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)  Could not resolve 'archive.canonical.com' 

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not resolve 'packages.medibuntu.org' 

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org' 

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org' 

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not resolve 'packages.medibuntu.org' 

W: Failed to fetch cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)/dists/gutsy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 

W: Failed to fetch cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)/dists/gutsy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 

W: Some index files failed to download, they have been ignored, or old ones used instead. 

The strange thing is:  if you see the last few options, it's saying "Gutsy Gibbon" "not "maverick Meerkat" Or "lucid lynx"

When adding CD ROMs, they DO show as the correct version names.

I've since removed all of the "Other Sources" And manually re-added 10.10 (for some reason 10.4 won't re-add to the "other sources" option, though there are 4 or 5 of them in the main source tab that I can't remove).

I wouldn't mind just wiping out and restarting with 10.10, but when I try to do the clean install, it doesn't recognize the original Ubuntu partition (assumes everything is my Windows partition).  I really don't want to redo the whole two systems to get it working, so any answer on getting past this, either with a clean ubuntu restart or getting the update manager to actually work with the CD would be appreciated.

---

