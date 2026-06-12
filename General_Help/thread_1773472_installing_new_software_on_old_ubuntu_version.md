---
title: "installing new software on old ubuntu version"
date: 2011-06-02
forum: General Help
---

### Post by cudaaar on 2011-06-02
Hi, 

I have an older version of ubuntu server.  I would like to install some software (gitosis).  Can't do this, because when I try to install I get error messages like this:

```

# sudo apt-get install gitosis
...
Err http://us.archive.ubuntu.com jaunty-updates/universe gitosis 0.2+20080825-2ubuntu0.1
  404 Not Found [IP: 91.189.92.161 80]
Fetched 23.8kB in 0s (26.1kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdigest-sha1-perl/libdigest-sha1-perl_2.11-2build2_amd64.deb  404 Not Found [IP: 91.189.92.161 80]
...

```The reason I don't want to upgrade is because I have a crappy raid card which only works with this outdated linux kernel

```

# uname -a
Linux xfel1 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

```I'd be happy to upgrade, if I can keep the same kernel.

I'd be happy to use old repositories, but I can't figure out how.

I'd consider using software raid, but this seems an extreme measure since I just want to install some very simple software (git, gitosis)

Thanks in advance for any help.

here is my /etc/apt/sources.list file:

```

# 
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release amd64 (20090421.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release amd64 (20090421.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by cudaaar on 2011-06-02
Bummer, no response.  Would greatly appreciate any suggestions.

Is it generally the case that software cannot be updated until Ubuntu is upgraded to the latest version?  Just trying to figure out if Ubuntu will work for my needs.  Maybe I'm doing something wrong here.

---

### Post by ckrul on 2011-06-07
I'm having the same problems updating APT too:
```

W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages  404 Not Found
W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages  404 Not Found
W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found
W: Failed to fetch http://nl.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found

```
I checked several mirrors in The Netherlands, and all are missing the Jaunty packages:
[http://ftp.telfort.nl/pub/mirror/ubuntu/dists/](http://ftp.telfort.nl/pub/mirror/ubuntu/dists/)
[http://ftp.tudelft.nl/archive.ubuntu.com/dists/](http://ftp.tudelft.nl/archive.ubuntu.com/dists/)

It seems like all packages of pre Karamic (9.10) releases are no longer available (except LTS releases). Also see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

So we're having a problem now since upgrading to a higher version requires the installation of packages (update-manager-core).
That sucks!

Anyone any idea how to get around this?

---

### Post by Bucky Ball on 2011-06-07
No longer supported you mean. Non-LTS releases are supported for 18 months (from memory but might not be that long).

If you are installing the latest version of some (not all) software the dependencies will probably not be met in the unsupported releases. There might be a way around that - download the required dependencies - but you could end up running in circles attempting to load the requirements for the dependencies and so on.

---

### Post by Zill on 2011-06-07
> **cudaaar said:**
> ...I'd be happy to use old repositories, but I can't figure out how...
As you know, Jaunty reached end-of-life on October 23, 2010 and so is no longer supported.

However, I believe old releases can be found at the following site:

[http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/")

No guarantees but I *think* you should be able to point your sources.list file to the appropriate jaunty repo(s) and then install your new app.

Of course, there *may* be significant security implications for using this unsupported release on a server.

---

