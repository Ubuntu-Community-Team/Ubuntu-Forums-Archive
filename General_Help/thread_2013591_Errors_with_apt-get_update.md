---
title: "Errors with apt-get update"
date: 2012-07-01
forum: General Help
---

### Post by BigBaka on 2012-07-01
Dear all,

I seem to continually get strange errors during the apt-get update process. Even though I'm at an internet cafe it seems that I always get errors. This is the end part of the readout from apt-get update. What is going on here?

```
Get:47 [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,847 B]
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                   
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                   
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-updates/universe Translation-en                                                                     
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/main Translation-en                                                                       
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                 
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                 
Hit [http://la.archive.ubuntu.com](http://la.archive.ubuntu.com) precise-backports/universe Translation-en                                                                   
Fetched 13.4 MB in 3min 14s (69.3 kB/s)                                                                                                      
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/source/Sources](http://packages.medibuntu.org/dists/precise/free/source/Sources)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/source/Sources](http://packages.medibuntu.org/dists/precise/non-free/source/Sources)  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_AU](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_AU)  Unable to connect to download.virtualbox.org:http:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en)  Unable to connect to download.virtualbox.org:http:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_CA](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_CA)  Unable to connect to download.virtualbox.org:http:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_GB](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_GB)  Unable to connect to download.virtualbox.org:http:

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_NZ](http://download.virtualbox.org/virtualbox/debian/dists/precise/contrib/i18n/Translation-en_NZ)  Unable to connect to download.virtualbox.org:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_CA](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_CA)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_NZ](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_NZ)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_CA](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_CA)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_NZ](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/i18n/Translation-en_NZ)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_CA](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_CA)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_NZ](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/i18n/Translation-en_NZ)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_CA](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_CA)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_NZ](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/i18n/Translation-en_NZ)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_AU](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_AU)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_CA](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_CA)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_NZ](http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/precise/main/i18n/Translation-en_NZ)  Unable to connect to ppa.launchpad.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
jvc@CountryRep:~$
```

---

### Post by BigBaka on 2012-07-01
using synaptic I get the following error message

```
GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:
```

---

### Post by matt_symes on 2012-07-01
Hi

> **BigBaka said:**
> using synaptic I get the following error message

```
GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:
Failed to fetch [http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/trebelnik-stefina/nightingale/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:
```

Firstly you are missing some public keys for your PPAs. You need to import them.

Open a terminal and type...

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C2518248EEA14886
```

Enter your password. It will not be echoed to the screen. Type this to get the other key

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220
```

Then type

```
sudo apt-get update
```

That should fix the first issue. Post back when done and on any errors and then we can look at the second problem.

Kind regards

---

