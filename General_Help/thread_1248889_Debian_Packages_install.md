---
title: "Debian Packages install"
date: 2009-08-24
forum: General Help
---

### Post by maxshn on 2009-08-24
Hi,

I was trying Debian lenny and I can't install packages I try with apt-get install and aptitude install the fist give error not found E: or something like that and the second just try and show me 0 packages installed what can I do?:confused:

There is a add/remove application like in Ubuntu ?
 and update manager also like ubuntu ?:?::shock:

---

### Post by Screwdriver0815 on 2009-08-25
> **maxshn said:**
> Hi,

I was trying Debian lenny and I can't install packages I try with apt-get install and aptitude install the fist give error not found E: or something like that and the second just try and show me 0 packages installed what can I do?:confused:

There is a add/remove application like in Ubuntu ?
 and update manager also like ubuntu ?:?::shock:

if apt-get/package manager does not find certain packages, then maybe you have to enable some repositories. This works the same way like in Ubuntu, but you need the deb-lines for Lenny (search for them at Debian website or in a Debian Forum)

update/add/remove manager: no, it is the other way around: Ubuntu uses the Debian package manager, because Ubuntu is based on Debian.

---

### Post by slakkie on 2009-08-25
I think your sources.list is a bit borked.

```

apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.0.1-1
  Version table:
     1.0.1-1 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

```

As for do-release-upgrade (the CLI update manager), seems like Ubuntu has the lead on that package. The do-release-upgrade file actually says on Debian:

```

$ python /usr/share/doc/update-manager-core/do-release-upgrade
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found
$ lsb_release -a
Distributor ID: Debian
Description:    Debian GNU/Linux 5.0.2 (lenny)
Release:        5.0.2
Codename:       lenny

```

Yes, that we can't upgrade to Ubuntu ;)

```

# On Ubuntu
apt-cache policy update-manager-core
update-manager-core:
  Installed: 1:0.124.8
  Candidate: 1:0.124.8
  Version table:
 *** 1:0.124.8 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status

# On Debian Lenny
update-manager-core:
  Installed: 0.68.debian-7
  Candidate: 0.68.debian-7
  Version table:
 *** 0.68.debian-7 0
        500 ftp://ftp.nl.debian.org lenny/main Packages
        100 /var/lib/dpkg/status

```

And on sid the package is at the same version as on Lenny.

---

