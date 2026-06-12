---
title: "Update key error"
date: 2009-12-12
forum: General Help
---

### Post by Weidbrewer on 2009-12-12
Trying to install updates 8.10 (64-bit), and I'm getting a couple of errors:

First, I'm getting the "Not all updates can be installed" error that gives the partial upgrade option or cancel.  PU starts, but then the window close and nothing happens.  If I hit "Close" and then "Check, I get these errors:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
```

I had been getting some other errors with mediabutu keys, but was able to Google and solve with:  

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

I couldn't find anything for the others.  Any help would be greatly appreciated.

---

### Post by slakkie on 2009-12-12
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

if the Ubuntu keyserver is acting up you could also use this keyserver: wwwkeys.eu.pgp.net

---

### Post by Weidbrewer on 2009-12-12
Thanks!  That got rid of the key error...now I'm just getting the "Partial upgrade" warning and can't seem to do anything from there.

[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/Untitled-2.jpg[/IMG]

---

### Post by colin.p on 2009-12-12
> **slakkie said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

if the Ubuntu keyserver is acting up you could also use this keyserver: wwwkeys.eu.pgp.net

Sorry to barge in on this conversation, but thanks for this tip. It worked perfectly, and no more error messages.

Colin

---

### Post by slakkie on 2009-12-12
> **Weidbrewer said:**
> Thanks!  That got rid of the key error...now I'm just getting the "Partial upgrade" warning and can't seem to do anything from there.

[http://i166.photobucket.com/albums/u105/Weidbrewer/Untitled-2.jpg](http://i166.photobucket.com/albums/u105/Weidbrewer/Untitled-2.jpg)
Could you run aptitude -s full-upgrade? This will simulate the action, so you can see what will happen if you allow the installation.

---

### Post by Weidbrewer on 2009-12-12
I think that this would be the important part:

```
Leave the following dependencies unresolved:
ubuntu-desktop recommends openoffice.org-calc
ubuntu-desktop recommends openoffice.org-impress
ubuntu-desktop recommends openoffice.org-math
ubuntu-desktop recommends openoffice.org-writer
Score is 5934

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  openoffice.org-common openoffice.org-core openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za python-uno 
The following NEW packages will be installed:
  libdns44{a} linux-headers-2.6.27-16{a} linux-headers-2.6.27-16-generic{a} 
  linux-image-2.6.27-16-generic{a} 
  linux-restricted-modules-2.6.27-16-generic 
The following packages will be REMOVED:
  openoffice.org-base-core{a} openoffice.org-calc{a} openoffice.org-draw{a} 
  openoffice.org-impress{a} openoffice.org-math{a} openoffice.org-writer{a} 
The following packages will be upgraded:
  bind9-host dnsutils libbind9-40 libdns43 libisc44 libisccc40 libisccfg40 
  liblwres40 linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic 
12 packages upgraded, 5 newly installed, 9 downgraded, 6 to remove and 0 not upgraded.
Need to get 85.9MB of archives. After unpacking 69.5MB will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```


Which is okay...but I can't get the up/downgrade to run.

---

### Post by slakkie on 2009-12-12
I want to see the full log

---

### Post by Weidbrewer on 2009-12-13
Here you go:

```
~$ aptitude -s full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  openoffice.org-core 
The following NEW packages will be installed:
  latex-xft-fonts{a} libdns44{a} linux-headers-2.6.27-16{a} 
  linux-headers-2.6.27-16-generic{a} linux-image-2.6.27-16-generic{a} 
  linux-restricted-modules-2.6.27-16-generic xfonts-mathml{a} 
The following packages will be upgraded:
  bind9-host dnsutils libbind9-40 libdns43 libisc44 libisccc40 libisccfg40 
  liblwres40 linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic openoffice.org-base-core 
  openoffice.org-calc openoffice.org-common openoffice.org-draw 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb 
  openoffice.org-help-en-us openoffice.org-impress 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math 
  openoffice.org-writer python-uno 
27 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 121MB of archives. After unpacking 181MB will be used.
The following packages have unmet dependencies:
  openoffice.org-core: Depends: libhunspell-1.1-0 (>= 1.1.6-1) which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
openoffice.org-base-core
openoffice.org-calc
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

Downgrade the following packages:
openoffice.org-common [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-core [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-gnome [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-gtk [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-help-en-gb [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-help-en-us [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-l10n-en-gb [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-l10n-en-za [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
python-uno [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends openoffice.org-calc
ubuntu-desktop recommends openoffice.org-impress
ubuntu-desktop recommends openoffice.org-math
ubuntu-desktop recommends openoffice.org-writer
Score is 5934

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  openoffice.org-common openoffice.org-core openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za python-uno 
The following NEW packages will be installed:
  libdns44{a} linux-headers-2.6.27-16{a} linux-headers-2.6.27-16-generic{a} 
  linux-image-2.6.27-16-generic{a} 
  linux-restricted-modules-2.6.27-16-generic 
The following packages will be REMOVED:
  openoffice.org-base-core{a} openoffice.org-calc{a} openoffice.org-draw{a} 
  openoffice.org-impress{a} openoffice.org-math{a} openoffice.org-writer{a} 
The following packages will be upgraded:
  bind9-host dnsutils libbind9-40 libdns43 libisc44 libisccc40 libisccfg40 
  liblwres40 linux-generic linux-headers-generic linux-image-generic 
  linux-restricted-modules-generic 
12 packages upgraded, 5 newly installed, 9 downgraded, 6 to remove and 0 not upgraded.
Need to get 85.9MB of archives. After unpacking 69.5MB will be used.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.
```

---

### Post by slakkie on 2009-12-14
Ok, let's narrow down what will be installed/removed by first doing:

sudo aptitude safe-upgrade

This will install everything without doing removal of packages which might be needed to upgrade some packages. Packages that will remove other packages will be "Held back".

Then rerun aptitude -s full-upgrade.

---

### Post by Weidbrewer on 2009-12-17
Oh, wow...I never got an email update for the thread, so I didn't know there was a reply here.  I will try to give this a shot later tonight.

---

### Post by Weidbrewer on 2009-12-19
Here is the printout of re-runnung it after your first step:

```
~$ sudo aptitude -s full-upgrade
[sudo] password for weidbrewer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  openoffice.org-core 
The following NEW packages will be installed:
  latex-xft-fonts{a} xfonts-mathml{a} 
The following packages will be upgraded:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common 
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-impress openoffice.org-l10n-en-gb 
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-writer 
  python-uno 
15 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 89.1MB of archives. After unpacking 14.0MB will be used.
The following packages have unmet dependencies:
  openoffice.org-core: Depends: libhunspell-1.1-0 (>= 1.1.6-1) which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
openoffice.org-base-core
openoffice.org-calc
openoffice.org-draw
openoffice.org-impress
openoffice.org-math
openoffice.org-writer

Downgrade the following packages:
openoffice.org-common [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-core [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-gnome [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-gtk [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]
openoffice.org-help-en-gb [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-help-en-us [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-l10n-en-gb [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
openoffice.org-l10n-en-za [1:3.1.0-3ubuntu2~intrepid1 (now) -> 1:2.4.1-9ubuntu1
(intrepid, intrepid)]
python-uno [1:3.1.0-5ubuntu1~intrepid1 (now) -> 1:2.4.1-11ubuntu2.2
(intrepid-updates, intrepid-security, intrepid-security, intrepid-updates)]

Leave the following dependencies unresolved:
ubuntu-desktop recommends openoffice.org-calc
ubuntu-desktop recommends openoffice.org-impress
ubuntu-desktop recommends openoffice.org-math
ubuntu-desktop recommends openoffice.org-writer
Score is 5934

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  openoffice.org-common openoffice.org-core openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za python-uno 
The following packages will be REMOVED:
  openoffice.org-base-core{a} openoffice.org-calc{a} openoffice.org-draw{a} 
  openoffice.org-impress{a} openoffice.org-math{a} openoffice.org-writer{a} 
0 packages upgraded, 0 newly installed, 9 downgraded, 6 to remove and 0 not upgraded.
Need to get 54.3MB of archives. After unpacking 97.8MB will be freed.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

---

