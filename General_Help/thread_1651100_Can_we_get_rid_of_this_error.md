---
title: "Can we get rid of this error?"
date: 2010-12-22
forum: General Help
---

### Post by sdowney717 on 2010-12-22
I have had it for quite a while and I run MM not karmic.

> Need to get 176kB of archives.
After this operation, 1,241kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/webupd8team/haguichi/ubuntu/](http://ppa.launchpad.net/webupd8team/haguichi/ubuntu/) maverick/main haguichi all 1.0.3-1~webupd8~maverick1 [176kB]
Fetched 176kB in 0s (209kB/s)   
warning, in file '/var/lib/dpkg/status' near line 51863 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 51864 package 'virtualbox-3.0':
 error in Config-Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 59866 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Selecting previously deselected package haguichi.
(Reading database ... 537845 files and directories currently installed.)
Unpacking haguichi (from .../haguichi_1.0.3-1~webupd8~maverick1_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
warning, in file '/var/lib/dpkg/status' near line 51863 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 51864 package 'virtualbox-3.0':
 error in Config-Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 59866 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Setting up haguichi (1.0.3-1~webupd8~maverick1) ...
scott@scott-desktop:~$ 


---

### Post by karthick87 on 2010-12-22
Try,
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
``````

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by bodhi.zazen on 2010-12-22
What is in /etc/apt/sources.lst

---

### Post by sdowney717 on 2010-12-22
here it is
> 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.




## Major bug fix updates produced after the final release of the
## distribution.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick universe
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-updates universe
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick multiverse
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick multiverse
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-updates multiverse
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner



deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-security universe
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-security universe
deb [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-security multiverse
deb-src [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://navit.latouche.info/ubuntu](http://navit.latouche.info/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu) karmic main # disabled on upgrade to maverick
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu](http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu) maverick main # disabled on upgrade to maverick
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) maverick partner

---

### Post by sdowney717 on 2010-12-22
to me it is a bizarre error and has simply hung around a long time but not stopping things from working
I used to have vbox installed, now it is not.

> warning, in file '/var/lib/dpkg/status' near line 51863 package 'virtualbox-3.0':
error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 51864 package 'virtualbox-3.0':
error in Config-Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 59866 package 'virtualbox-3.0':
error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number

---

### Post by bodhi.zazen on 2010-12-22
I do not see any obvious problem with that.

I would make a small suggestion, unless you are compiling from source you can comment out all the deb-src lines.

I would tend to clean house a bit and remove all the lucid and karmic lines, but so long as they are commented out it should not make a difference.

I would purge and re-install virtualbox.

---

### Post by sdowney717 on 2010-12-22
that is interesting message from synaptic
> Package virtualbox-3.0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by plucky on 2010-12-23
> **sdowney717 said:**
> that is interesting message from synaptic


If you are confident to edit system files:-

You could try to edit the status file and correct the problem with the version line.

[color=blue]Please make a backup copy first so that if you make a mistake you can revert back the status file.[/color]

> warning, in file '/var/lib/dpkg/status' near line 51863 package 'virtualbox-3.0':
error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number

Probably the _ instead of the ~

This is how my version line looks ```
Version: 3.2.12-68302~Ubuntu~karmic
``` running on Lucid with Virtualbox 3.2.12.

Good Luck

---

### Post by sdowney717 on 2010-12-23
Thanks, sure, I will give that a go.
where and what is the file name?

I am going out of town so It will be a week before I get back to this PC, please let me know anyway.

---

### Post by sdowney717 on 2010-12-23
ok, I found the file and edited with sudo
BUT BUT BUT!, it still claims those little underscores are there and I did change them to tilde. And I did a reboot .

screenshot




> scott@scott-desktop:~$ sudo apt-get remove aa3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavutil-extra-49 libx264-67 vamps libimobiledevice0 mkvtoolnix
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  aa3d
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 77.8kB disk space will be freed.
Do you want to continue [Y/n]? y
warning, in file '/var/lib/dpkg/available' near line 59961 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
(Reading database ... 540828 files and directories currently installed.)
Removing aa3d ...
Processing triggers for man-db ...


this is the text in status file related to virtualbox
> Package: virtualbox-3.0
Status: deinstall ok config-files
Priority: optional
Section: non-free/misc
Installed-Size: 84800
Maintainer: Sun Microsystems, Inc. <info@virtualbox.org>
Architecture: i386
Version: 3.0.10-54097~Ubuntu~karmic
Config-Version: 3.0.10-54097~Ubuntu~karmic
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.7), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libpython2.6 (>= 2.6), libqt4-network (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libsdl1.2debian (>= 1.2.10-1), libssl0.9.8 (>= 0.9.8f-5), libstdc++6 (>= 4.4.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxml2 (>= 2.7.4), libxmu6, libxslt1.1 (>= 1.1.18), libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, libhal1 (>= 0.5), pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-ose
Conffiles:
 /etc/init.d/vboxdrv 7d496447073c95f3c0658410671ea966
Description: Sun VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Python-Version: >= 2.4

---

### Post by sdowney717 on 2010-12-23
it does not recognize some changes made to the status file, I just put your complete line in there and still it says this
 
error in Config-Version string '3.2.12-68302_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 59961 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
(Reading database ... 540828 files and directories currently installed.)
Removing aa3d ...


so I completely deleted virtualbox-3.0 out of that list and then it says this

warning, in file '/var/lib/dpkg/available' near line 59961 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Selecting previously deselected package aa3d.
(Reading database ... 540819 files and directories currently installed.)
Unpacking aa3d (from .../archives/aa3d_1.0-8_i386.deb) ...
Processing triggers for man-db ...
warning, in file '/var/lib/dpkg/available' near line 59961 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Setting up aa3d (1.0-8) ...

---

### Post by sdowney717 on 2010-12-23
OK, I found it. there is another file called available. I changed to tilde and it works without an error.

---

### Post by sdowney717 on 2010-12-23
anyway, I though maybe put that text block back into the status file, but gives me weird errors and dpkg bombs, so can we just leave it out?

> Need to get 0B/9,158B of archives.
After this operation, 77.8kB of additional disk space will be used.
warning, in file '/var/lib/dpkg/status' near line 9 package 'virtualbox-3.0':
 error in Config-Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
dpkg: parse error, in file '/var/lib/dpkg/status' near line 12 package 'virtualbox-3.0':
 `Depends' field, reference to `libxslt1.1': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)


---

### Post by matt_symes on 2010-12-23
Hi

I don't think it likes the tilda ~ try a hypen - instead in the two files for the version

Kind regards

---

### Post by sdowney717 on 2010-12-23
down to this here, but getting error
anything in there looking wrong?
can you post yours?

dpkg: parse error, in file '/var/lib/dpkg/status' near line 18 package 'virtualbox-3.0':
 field name `VirtualBox' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

> Package: virtualbox-3.0
Status: deinstall ok config-files
Priority: optional
Section: non-free/misc
Installed-Size: 84800
Maintainer: Sun Microsystems, Inc. <info@virtualbox.org>
Architecture: i386
Version: 3.0.10-54097~Ubuntu~karmic
Config-Version: 3.0.10-54097~Ubuntu~karmic
Replaces: virtualbox
Provides: virtualbox
Depends: libc6 (>= 2.7), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libpython2.6 (>= 2.6), libqt4-network (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libsdl1.2debian (>= 1.2.10-1), libssl0.9.8 (>= 0.9.8f-5), libstdc++6 (>= 4.4.0), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxml2 (>= 2.7.4), libxmu6, libxslt1.1 (>= 1.1.1), libxt6, zlib1g (>= 1:1.1.4), psmisc, adduser
Pre-Depends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, libhal1 (>= 0.5), pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-ose
Conffiles:
/etc/init.d/vboxdrv: 7d496447073c95f3c0658410671ea966
Description: Sun VirtualBox
VirtualBox is a powerful PC virtualization solution allowing you to run a
wide range of PC operating systems on your Linux system. This includes
Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
feature set and excellent performance, making it the premier virtualization
software solution on the market.
Python-Version: >= 2.4 

---

### Post by sdowney717 on 2010-12-23
switched to hyphen but still give syntax error

what if I just leave the whole vbox text block out of the list?
If I do that, dpkg works. Will it affect anything? like installing vbox?

---

### Post by matt_symes on 2010-12-23
Hi

Make a backup of both status and available files and then remove  the offending entry from both. 
It is saying it is uninstalled but just has config files and you can search for them later if they exist. 

Remove all text from start of Package to end of description for the virtual box entry.

Kind regards

---

### Post by sdowney717 on 2010-12-23
thanks!

---

### Post by matt_symes on 2010-12-23
Hi

No worries. Can you mark it as solved.

Kind regards

---

