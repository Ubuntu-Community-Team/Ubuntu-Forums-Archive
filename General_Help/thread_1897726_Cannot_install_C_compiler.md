---
title: "Cannot install C compiler"
date: 2011-12-19
forum: General Help
---

### Post by zac2290 on 2011-12-19
I cannot seem to install a C compiler.

I have tried installing build-essential but receive the following:

```
 sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
```

So I tried manually downloading and installing it with ./configure but got:

```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for dpkg-architecture... no
configure: error: The dpkg development files (dpkg-dev) must be installed to build this package.

```

Tried using apt-get to install dpgk-dev..

```
sudo apt-get install dpkg-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dpkg-dev: Depends: xz-utils but it is not installable
            Recommends: gcc but it is not installable or
                        c-compiler but it is not installable
            Recommends: build-essential but it is not installable
            Recommends: fakeroot but it is not installable
E: Broken packages

```

Same thing happens when I try to install gcc etc. Any other package I try to install requires a C compiler but I cant seem to install one.

Any advice welcome!

---

### Post by seawolf167 on 2011-12-19
Can you run 

```
sudo apt-get update && sudo apt-get install build-essential
```and post the output here

---

### Post by zac2290 on 2011-12-19
```
sudo apt-get update
Err http://non-us.debian.org stable Release.gpg
  Could not resolve 'non-us.debian.org'
Err http://non-us.debian.org/debian-non-US/ stable/non-US Translation-en_US
  Could not resolve 'non-us.debian.org'
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://ftp.debian.org etch Release.gpg
Ign http://ftp.debian.org/ etch/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release [44.7kB]
Ign http://ftp.debian.org etch Release
Ign http://ftp.debian.org etch/main Packages
Ign http://www.us.debian.org stable Release.gpg
Ign http://ftp.debian.org etch/main Packages
Ign http://www.us.debian.org/debian/ stable/main Translation-en_US
Ign http://www.us.debian.org/debian/ stable/contrib Translation-en_US
Ign http://www.us.debian.org/debian/ stable/non-free Translation-en_US
Err http://ftp.debian.org etch/main Packages
  404  Not Found
Get:3 http://security.ubuntu.com lucid-security/main Packages [250kB]
Ign http://www.us.debian.org stable Release
Get:4 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:5 http://security.ubuntu.com lucid-security/main Sources [72.5kB]
Get:6 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:7 http://security.ubuntu.com lucid-security/universe Packages [111kB]
Ign http://www.us.debian.org stable/main Packages
Get:8 http://security.ubuntu.com lucid-security/universe Sources [27.6kB]
Get:9 http://security.ubuntu.com lucid-security/multiverse Packages [4,423B]
Get:10 http://security.ubuntu.com lucid-security/multiverse Sources [1,750B]
Ign http://www.us.debian.org stable/contrib Packages
Ign http://www.us.debian.org stable/non-free Packages
Ign http://www.us.debian.org stable/main Packages
Ign http://www.us.debian.org stable/contrib Packages
Ign http://www.us.debian.org stable/non-free Packages
Err http://www.us.debian.org stable/main Packages
  404  Not Found [IP: 206.12.19.7 80]
Err http://www.us.debian.org stable/contrib Packages
  404  Not Found [IP: 206.12.19.7 80]
Err http://www.us.debian.org stable/non-free Packages
  404  Not Found [IP: 206.12.19.7 80]
Fetched 512kB in 2s (184kB/s)
Reading package lists... Done
W: Failed to fetch http://non-us.debian.org/debian-non-US/dists/stable/Release.gpg  Could not resolve 'non-us.debian.org'

W: Failed to fetch http://non-us.debian.org/debian-non-US/dists/stable/non-US/i18n/Translation-en_US.bz2  Could not resolve 'non-us.debian.org'

W: Failed to fetch http://ftp.debian.org/dists/etch/main/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://www.us.debian.org/debian/dists/stable/main/binary-amd64/Packages.gz  404  Not Found [IP: 206.12.19.7 80]

W: Failed to fetch http://www.us.debian.org/debian/dists/stable/contrib/binary-amd64/Packages.gz  404  Not Found [IP: 206.12.19.7 80]

W: Failed to fetch http://www.us.debian.org/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 206.12.19.7 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

```
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```

---

### Post by seawolf167 on 2011-12-19
You are getting a lot of failed to fetch results from the update command as well as a lot of Debian hits - what distro version are you using?

You can generate a new sources.list file in the mean time to check that the defaults work. Go [here]("http://repogen.simplylinux.ch/"), generate the list, then backup and create a new sources.list file

backup:
```
cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

make a new list:
```
gedit /etc/apt/sources.list
```

and overwrite the contents with your new list

then try running the update and install command

---

### Post by zac2290 on 2011-12-19
I am running Ubuntu 10.04 Lucid

Updating my source.list did the trick! Everything installed just fine!

You're my hero! Thank you very much for your help!

---

### Post by seawolf167 on 2011-12-19
Awesome :) please mark this thread as solved under thread tools.

---

