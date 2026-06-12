---
title: "Server 10.04LTS A error occurred during the signature verification"
date: 2011-01-23
forum: General Help
---

### Post by gaming_guy on 2011-01-23
Hi all,

I currently have a problem with running apt-get update on a fresh install of 10.04 LTS Server where I get the following error messages:

```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 2

W: GPG error: http://archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

When I run apt-get upgrade, I also get the unauthenticated pacakges warning:

```

WARNING: The following packages cannot be authenticated!
  libpam-modules base-files coreutils libc-bin libc6 tzdata libdevmapper1.02.1
  grub-pc libfreetype6 grub-common dpkg e2fslibs e2fsprogs gzip mount tar
  libdbus-1-3 libudev0 ifupdown fuse-utils libfuse2 util-linux udev dmsetup
  libglib2.0-0 libusb-0.1-4 plymouth libpng12-0 libplymouth2 mountall upstart
  bsdutils apt libssl0.9.8 libuuid1 libblkid1 libcomerr2 libpam-runtime
  libpam0g libss2 apt-utils bzip2 libbz2-1.0 libk5crypto3 libgssapi-krb5-2
  libkrb5-3 libkrb5support0 libldap-2.4-2 rsyslog ureadahead wget
  apt-transport-https at libxml2 dnsutils bind9-host bind9 libisc60 libisccc60
  libisccfg60 liblwres60 bind9utils libdns64 libbind9-60 python-apt
  language-selector-common man-db openssh-server openssh-client
  libparted0debian1 parted plymouth-theme-ubuntu-text update-manager-core w3m
  bind9-doc screen byobu libavahi-common-data libavahi-common3
  libavahi-client3 libcups2 libpcsclite1 smbfs smbclient samba-common-bin
  update-inetd samba libpam-smbpass winbind samba-common libwbclient0
  libwww-perl linux-firmware openssl python-lazr.restfulclient samba-doc sudo
  unattended-upgrades uuid-runtime apparmor libapparmor1 libapparmor-perl
  apparmor-utils
Install these packages without verification [y/N]? 


```

I have tried various things posted (apt-get clean etc), but none of them seem to work (including changing all gb.archive.ubuntu.com references to archive.ubuntu.com). Does anyone have any other things that I can try to see if it resolves the problem?

Thanks for reading,
g_g

(for anyone who needs it, the sources.list is below)

My sources.list:
```

 
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ $

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ l$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid universe
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by physeetcosmo on 2011-02-15
Hello,

I was having the same issue. I found your thread then went looking for an answer.

I found [this]("http://ubuntuforums.org/showthread.php?t=139191") thread that seemed to work for me.

Basically, run these commands in order:
```
$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
$ sudo touch /etc/apt/source.list
$ sudo apt-get update
$ sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get upgrade (or dist-upgrade)
```

Not sure why this works and why the authentication cleared up. Maybe some stale hash gets cleared?

Hope this works for you too!

---

### Post by gaming_guy on 2011-04-16
> **physeetcosmo said:**
> Hello,

I was having the same issue. I found your thread then went looking for an answer.

I found [this]("http://ubuntuforums.org/showthread.php?t=139191") thread that seemed to work for me.

Basically, run these commands in order:
```
$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
$ sudo touch /etc/apt/source.list
$ sudo apt-get update
$ sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get upgrade (or dist-upgrade)
```

Not sure why this works and why the authentication cleared up. Maybe some stale hash gets cleared?

Hope this works for you too!

Thanks for the reply, although I eventually tracked it down to the transparent proxy server I was using (Smoothwall Express with an old version of a proxy addon). Since removing SWE and changing my ISP, the problem no longer occurs under Debian & Ubuntu.


g_g

---

### Post by isparkes on 2011-07-13
I tried all this out and it didn't fix anything.

I then found that I had an out of date password for my proxy server in the file

```
etc/apt/apt.conf
```

Hope this helps someone

---

### Post by oaxacamatt1 on 2011-08-12
Yes, This works for me too.  Every couple of months I have to do this for the last several distros of Unbuntu.  I drives me a little batty.
Cheers,
Matt

---

### Post by cladiron on 2012-10-10
Just wanted to say, i had this same problem.
My fix was to just login into SSH and run "apt-get update"

---

