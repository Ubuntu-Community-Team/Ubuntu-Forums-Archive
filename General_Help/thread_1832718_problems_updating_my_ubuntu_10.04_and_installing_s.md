---
title: "problems updating my ubuntu 10.04 and installing some software"
date: 2011-08-25
forum: General Help
---

### Post by zicoe on 2011-08-25
Hey there.
Everytime i try to update my ubuntu 10.04 it hits me with the following error and i don't know what do anymore,

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7AGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234CGPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CFFailed to fetch [http://ppa.launchpad.net/example/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/example/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Can somebody rescue me please. Today i wanted to install KDE and it says

 "The action would require the installation of packages from not authenticated sources." 

when i click on OK it closes the message and does nothing. I suspect the root cause for these errors is the same. Anyone?

---

### Post by Cpierce on 2011-08-25
see if this helps:

[http://ubuntuforums.org/showthread.php?t=1815224](http://ubuntuforums.org/showthread.php?t=1815224)

---

### Post by zicoe on 2011-08-25
This is what i entered:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2836CB0A8AC93F7A 531EE72F4C9D234C A8A515F046D7E7CF

And this is what i got in return:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2836CB0A8AC93F7A 531EE72F4C9D234C A8A515F046D7E7CF
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: requesting key 46D7E7CF from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

But i am very sure that i have internet connection because i am using the same laptop to to get into the forum.

---

