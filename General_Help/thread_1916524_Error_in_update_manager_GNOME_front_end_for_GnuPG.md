---
title: "Error in update manager: GNOME front end for GnuPG"
date: 2012-01-28
forum: General Help
---

### Post by NautiusMaximus on 2012-01-28
My update manager is recommending that I install an update called "GNOME front end for GnuPG". When I try, it gives an error message "The package system is broken", and recommends that I try running 

```
apt-get install -f
```

from a terminal. When I do, I get the following output, which again shows an error:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  seahorse
Suggested packages:
  seahorse-plugins
The following packages will be upgraded:
  seahorse
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
109 not fully installed or removed.
Need to get 0 B/484 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: parsing file '/var/lib/dpkg/status' near line 5519 package 'seahorse':
 `Depends' field, invalid package name `libldap-2.4-"': character `"' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Any ideas what's going on here? Does any of this matter? And if so, how do I fix it?

I'm using Ubuntu 11.10.

Many thanks
NM

---

### Post by plucky on 2012-01-28
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 5519 package 'seahorse':
 `Depends' field, invalid package name `libldap-2.4-"': character `"' not allowed (only letters, digits and characters `-+._')

You can edit the status file using ```
gksudo gedit /var/lib/dpkg/status
``` and search for line 5519.

**libldap-2.4-"** should be **libldap-2.4-2** there should not be a " at the end.

This is what mine looks like ```
Package: seahorse
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 2140
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 3.2.2-0ubuntu0.1
Depends: libatk1.0-0 (>= 1.12.4), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.7), libgck-1-0 (>= 3.1.4), libgcr-3-1 (>= 3.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0), libgnome-keyring0 (>= 3.0.0), libgpgme11 (>= 1.2.0), libgtk-3-0 (>= 3.0.0), liblaunchpad-integration-3.0-1 (>= 0.1.17),[color=red] libldap-2.4-2 (>= 2.4.7)[/color], libsoup2.4-1 (>= 2.4.0), dconf-gsettings-backend | gsettings-backend, gnupg (>= 1.4.7), gnome-keyring (>> 3.1.90)]
```


Or you could just try to run from a terminal ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then run ```
sudo apt-get update
``` and see if you get the same error.

Good Luck

---

### Post by NautiusMaximus on 2012-01-28
Thanks very much plucky! I edited the file with gedit as you suggested, and that fixed it.

Simple when you know how, isn't it?

Thanks
NM

---

