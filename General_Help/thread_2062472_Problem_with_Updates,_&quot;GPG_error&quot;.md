---
title: "Problem with Updates, &quot;GPG error&quot;"
date: 2012-09-25
forum: General Help
---

### Post by Alcidious on 2012-09-25
Running Ubuntu 12.04 32-bit on a samsung laptop. I am trying to update my kernel in order to install the kernel with the fix (3.2.31, i think).  But whenever I try to run sudo apt-get update I get the following error:


Fetched 154 kB in 2s (60.9 kB/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

I also tried to update using the update manager, and I get the following error:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
----Details----
dbus dbus-x11 ghostscript ghostscript-cups ghostscript-x isc-dhcp-client isc-dhcp-common libdbus-1-3 libdbus-1-dev libgs9 libgs9-common linux-headers-3.2.0-31 linux-headers-3.2.0-31-generic-pae linux-headers-generic-pae linux-libc-dev resolvconf software-center tzdata tzdata-java

Any help is appreciated! Hopefully with this update I will have a bug-free system again (fingers crossed)

---

### Post by einonm on 2012-09-25
Did you try googling any of your errors? A simple search for your error message gave the top answer of:

[http://techpad.co.uk/content.php?sid=84](http://techpad.co.uk/content.php?sid=84)

Which looks promising.

---

### Post by Alcidious on 2012-09-25
By the way, looking at other posts with similar errors, I ran:

sudo apt-get update
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

no luck

and also:

sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update

and also no luck.

---

### Post by jerrrys on 2012-09-25
try here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by wojox on 2012-09-25
Add the keys back:
```
gpg --keyserver pgpkeys.mit.edu --recv-key  40976EAF437D05B5     
gpg -a --export 010908312D230C5F | sudo apt-key add -
```

---

### Post by Alcidious on 2012-09-26
Sweet! Fixed, thanks y'all!

---

