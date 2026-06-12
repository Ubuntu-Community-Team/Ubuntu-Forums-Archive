---
title: "Problems with update manager and ifuse."
date: 2010-05-16
forum: General Help
---

### Post by FraidoCat on 2010-05-16
Every time I check for updates, I get his error. 

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EA3A911D48B8E25
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Also, when I try to install ifuse using a command line so I can access my music and photos from my ipod touch I get the following errors. *errors are in bold at the bottom*

>  sudo apt-get install ifuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libplist0 libclucene0ldbl libxine1-x kdebase-runtime-data-common
  libxine1-misc-plugins libxcb-xv0 kde-icons-oxygen libxine1-bin libexiv2-5
  liblzma0 kdelibs5-data libusbmux0 libxcb-shape0 exiv2 libxcb-shm0
  kdebase-runtime-data libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libimobiledevice0 libusbmuxd1
The following NEW packages will be installed:
  ifuse libimobiledevice0 libusbmuxd1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/62.9kB of archives.
After this operation, 295kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libimobiledevice0
Install these packages without verification [y/N]? y
(Reading database ... 129756 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Selecting previously deselected package libimobiledevice0.
Unpacking libimobiledevice0 (from .../libimobiledevice0_0.9.7-1ubuntu1~ppa2_i386.deb) ...
Selecting previously deselected package ifuse.
Unpacking ifuse (from .../ifuse_0.9.7-1ubuntu1~ppa1_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 2556
[B]Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1[/B])


I'm a noob, so any help is appreciated.

---

### Post by neo unplugged on 2010-05-18
Am not an expert but I found a similar problem at the following location
gpg --export --armor 0c713da6 | sudo apt-key add -

Try the following, it might work:

gpg --keyserver keyserver.ubuntu.com --recv 6E80C6B7
gpg --export --armor 6E80C6B7 | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv D48B8E25
gpg --export --armor D48B8E25 | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv F9CB8DB0
gpg --export --armor F9CB8DB0 | sudo apt-key add -
			 				 sudo apt-get install ifuse

---

### Post by mac9416 on 2010-05-18
Hi, FraidoCat,

I think neo unplugged has helped you with the first error. The second one *seems* to be a problem with a package having been corrupted during downloading. To clear out the package cache and force APT to re-download the package, run this command:

```
$ apt-get clean
```

---

### Post by FraidoCat on 2010-05-18
Thanks. So I just did what neo suggested. Don't know if it worked. Everytime plug in my ipod touch 
i am prompted to oped fspot for photos. When I click on the ipod link. The only folder is DCIM. Whatever that it. 

Thanks for trying guys.

---

### Post by Yellow Pasque on 2010-05-18
> trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
^It looks like an old package is preventing the install of a package you need, so:
```
sudo apt-get remove --purge libusbmux0
sudo apt-get install ifuse
```

---

