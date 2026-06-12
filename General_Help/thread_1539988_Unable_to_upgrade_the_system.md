---
title: "Unable to upgrade the system"
date: 2010-07-27
forum: General Help
---

### Post by manolomanolo on 2010-07-27
Hi to all.

After running "sudo apt-get update" I try and run "sudo apt-get upgrade" but I get the following errors:

```
**mano@mano-laptop:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  vlc-plugin-pulse: Depends: vlc-nox (= 1.1.1-1~lffl~lucid~ppa) but 1.1.0-1~lffl~lucid~ppa is installed
E: Unmet dependencies. Try using -f.

**mano@mano-laptop:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  python-libmimic python-sexy
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  vlc vlc-nox
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following packages will be upgraded:
  vlc vlc-nox
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/5192kB of archives.
After this operation, 324kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 236450 files and directories currently installed.)
Preparing to replace vlc 1.1.0-1~lffl~lucid~ppa (using .../vlc_1.1.1-1~lffl~lucid~ppa_amd64.deb) ...
Unpacking replacement vlc ...
dpkg: error processing /var/cache/apt/archives/vlc_1.1.1-1~lffl~lucid~ppa_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/vlc/plugins/codec/libsdl_image_plugin.so', which is also in package vlc-nox 0:1.1.0-1~lffl~lucid~ppa
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace vlc-nox 1.1.0-1~lffl~lucid~ppa (using .../vlc-nox_1.1.1-1~lffl~lucid~ppa_amd64.deb) ...
Unpacking replacement vlc-nox ...
dpkg: error processing /var/cache/apt/archives/vlc-nox_1.1.1-1~lffl~lucid~ppa_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/vlc/plugins/codec/libx264_plugin.so', which is also in package vlc 0:1.1.0-1~lffl~lucid~ppa
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/vlc_1.1.1-1~lffl~lucid~ppa_amd64.deb
 /var/cache/apt/archives/vlc-nox_1.1.1-1~lffl~lucid~ppa_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

**mano@mano-laptop:~$**
```

The errors prevent me to execute other "apt-get" operations, such as "apt-get autoremove".

Any suggestion, please?
Thanks

---

### Post by dino99 on 2010-07-27
the error is due to this ppa, so desactivate it then update again (check that ppa still existed and maintained)

---

### Post by manolomanolo on 2010-07-27
Dino, thanks for your reply.
```

mano@mano-laptop:/etc/apt/sources.list.d$ ls
ailurus-ppa-lucid.list                           gezakovacs-pdfocr-lucid.list            minitube-neversfelde-ppa.list
ailurus-ppa-lucid.list.save                      gezakovacs-pdfocr-lucid.list.save       minitube-neversfelde-ppa.list.save
amandeepgrewal-notifyosdconfig-lucid.list        jd-team-jdownloader-lucid.list          tualatrix-ppa-lucid.list
amandeepgrewal-notifyosdconfig-lucid.list.save   jd-team-jdownloader-lucid.list.save     tualatrix-ppa-lucid.list.save
bean123ch-burg-lucid.list                        jonoomph-openshot-edge-lucid.list       ubuntu-wine-ppa-lucid.list
bean123ch-burg-lucid.list.save                   jonoomph-openshot-edge-lucid.list.save  ubuntu-wine-ppa-lucid.list.save
ferramroberto-linuxfreedomlucid-lucid.list       medibuntu.list
ferramroberto-linuxfreedomlucid-lucid.list.save  medibuntu.list.save
mano@mano-laptop:/etc/apt/sources.list.d$ cd ..
mano@mano-laptop:/etc/apt$ ls
apt.conf.d  preferences.d  secring.gpg  sources.list  sources.list.d  sources.list.save  trustdb.gpg  trusted.gpg  trusted.gpg~  trusted.gpg.d
mano@mano-laptop:/etc/apt$ cat sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid universe
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://it.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

What should I remove?
How should I check the ppa is still active?

Thanks.

---

### Post by wojox on 2010-07-27
Go into Software Sources > Other Software and uncheck the ppa's

---

### Post by dino99 on 2010-07-27
into synaptic repo tab: check the "LFFL" ppa and desactivate it (cant find it with launchpad) and use this one instead:

[https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc)

---

### Post by manolomanolo on 2010-07-27
Please see the attachment.

Should I uncheck all?

---

### Post by dino99 on 2010-07-27
take time to use synaptic: on the left side panel , choose "origine" to know which ppa owned "vlc", then you will know which ppa to uncheck

---

### Post by manolomanolo on 2010-07-27
Hi Dino. I did not add the PPA you suggested me. Thanks to your advices I just removed this one:

[http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu)

And everything works fine now.
However I still do not understand why I the error messages referred to some "lffl" PPA and why I found no related line in Software Sources, in the /etc/apt/sources.list file nor in the sources.list.d folder...

---

### Post by wojox on 2010-07-27
> **manolomanolo said:**
> Hi Dino. I did not add the PPA you suggested me. Thanks to your advices I just removed this one:

[http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu)

And everything works fine now.
However I still do not understand why I the error messages referred to some "lffl" PPA and why I found no related line in Software Sources, in the /etc/apt/sources.list file nor in the sources.list.d folder...

Yeah I stared at that file to and wondered why there was no ppa for vlc.  :confused:

---

### Post by dino99 on 2010-07-27
i guess its an old package from a previous distro as that ppa dont exist now, you might use only trusted and maintained ppa

---

