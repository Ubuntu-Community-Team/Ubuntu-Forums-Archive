---
title: "is medibuntu-key required in 12.04"
date: 2012-05-03
forum: General Help
---

### Post by jon zendatta on 2012-05-03
Hi all

I have installed ubuntu-restricted-extras

Do I require medibuntu-key for 12.04?

I ask this because I cannot get response from medibuntu server

Cheers:KS

---

### Post by 2ta8gdfte on 2012-05-03
Here is the medibuntu link that makes things a bit easier, and here is the command you need to add the key.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by jon zendatta on 2012-05-03
thanks for the reply. yes that was the command I'd issued!

```
 sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for j0n: 
--2012-05-04 15:27:45--  http://www.medibuntu.org/sources.list.d/precise.list
Resolving www.medibuntu.org (www.medibuntu.org)... 1.0.0.0
Connecting to www.medibuntu.org (www.medibuntu.org)|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.
```

this what I pasted:
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

---

### Post by plucky on 2012-05-04
> Resolving [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org](www.medibuntu.org))... 1.0.0.0
Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|1.0.0.0|:80](www.medibuntu.org)|1.0.0.0|:80)... connected.

Are you behind a proxy server?

Can you ping medibuntu.org ```
ping -c 5 medibuntu.org
```

It looks as though the command didn't complete correctly.

This is what I get when I run that command ```
--2012-05-04 09:22:23--  http://www.medibuntu.org/sources.list.d/precise.list
Resolving www.medibuntu.org (www.medibuntu.org)... 88.191.127.22
Connecting to www.medibuntu.org (www.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 284 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 284         --.-K/s   in 0s      

2012-05-04 09:22:24 (9.50 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [284/284]

Ign http://ppa.launchpad.net precise InRelease
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://extras.ubuntu.com precise InRelease
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://ppa.launchpad.net precise Release
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg
Ign http://archive.canonical.com precise InRelease
Hit http://extras.ubuntu.com precise Release
Hit http://packages.medibuntu.org precise InRelease
Hit http://gb.archive.ubuntu.com precise Release
Hit http://archive.canonical.com precise Release.gpg
Hit http://gb.archive.ubuntu.com precise-updates Release
Hit http://archive.canonical.com precise Release
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://ppa.launchpad.net precise/main Sources
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Sources
Hit http://packages.medibuntu.org precise/free i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted Sources
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.canonical.com precise/partner i386 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/main Sources
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://packages.medibuntu.org precise/non-free i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Ign http://packages.medibuntu.org precise/free TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_GB
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_GB
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free Translation-en
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Ign http://extras.ubuntu.com precise InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://ppa.launchpad.net precise InRelease
Ign http://archive.canonical.com precise InRelease
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://archive.canonical.com precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://packages.medibuntu.org precise InRelease
Hit http://gb.archive.ubuntu.com precise Release
Hit http://gb.archive.ubuntu.com precise-updates Release
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://archive.canonical.com precise/partner i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gb.archive.ubuntu.com precise/main Sources
Hit http://packages.medibuntu.org precise/free i386 Packages
Ign http://extras.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Sources
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/main Sources
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://packages.medibuntu.org precise/non-free i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Ign http://archive.canonical.com precise/partner Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://packages.medibuntu.org precise/free TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Ign http://packages.medibuntu.org precise/free Translation-en_GB
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free Translation-en
Reading package lists...

```

Good Luck

---

### Post by jon zendatta on 2012-05-04
```
 ping -c 5 medibuntu.org
PING medibuntu.org (88.191.127.22) 56(84) bytes of data.
64 bytes from medibuntu.org (88.191.127.22): icmp_req=1 ttl=41 time=336 ms
64 bytes from medibuntu.org (88.191.127.22): icmp_req=2 ttl=41 time=332 ms
64 bytes from medibuntu.org (88.191.127.22): icmp_req=3 ttl=41 time=331 ms
64 bytes from medibuntu.org (88.191.127.22): icmp_req=4 ttl=41 time=331 ms
64 bytes from medibuntu.org (88.191.127.22): icmp_req=5 ttl=41 time=328 ms

--- medibuntu.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 328.988/332.352/336.862/2.697 ms
```


 ```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2012-05-05 04:55:27--  http://www.medibuntu.org/sources.list.d/precise.list
Resolving www.medibuntu.org (www.medibuntu.org)... 1.0.0.0
Connecting to www.medibuntu.org (www.medibuntu.org)|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--2012-05-05 04:55:42--  (try: 2)  http://www.medibuntu.org/sources.list.d/precise.list
Connecting to www.medibuntu.org (www.medibuntu.org)|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--2012-05-05 04:55:56--  (try: 3)  http://www.medibuntu.org/sources.list.d/precise.list
Connecting to www.medibuntu.org (www.medibuntu.org)|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--2012-05-05 04:56:12--  (try: 4)  http://www.medibuntu.org/sources.list.d/precise.list
Connecting to www.medibuntu.org (www.medibuntu.org)|1.0.0.0|:80... connected.
HTTP request sent, awaiting response...
```

weird problem still exists

---

### Post by plucky on 2012-05-04
> Connecting to [www.medibuntu.org](www.medibuntu.org) ([www.medibuntu.org)|1.0.0.0|:80](www.medibuntu.org)|1.0.0.0|:80)... connected.

Should be medibuntu.org (88.191.127.22)


Have you installed anything to set up a proxy server?

Open a terminal and run ```
sudo apt-get --allow-unauthenticated install medibuntu-keyring
``` and post output.

---

### Post by jon zendatta on 2012-05-04
```
 sudo apt-get --allow-unauthenticated install medibuntu-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package medibuntu-keyring
```
 no proxy sever. fresh install

---

### Post by jon zendatta on 2012-05-04
i tried adding the ubuntu IP address in to hosts file:
```
echo "88.191.101.8 packages.medibuntu.org" | sudo tee -a /etc/hosts
```
then tried changing apt configuration, to use alternative port:
```
deb http://packages.medibuntu.org:8080 precise free non-free
```

---

### Post by jon zendatta on 2012-05-04
so then I tried
```
wget http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages
```

It appeared to work but when i did update && upgrade:
```
Some index files failed to download. They have been ignored, or old ones used instead
```

---

### Post by jon zendatta on 2012-05-04
Thanks all for your help. Removed the port 8080 from apt list, & have host file altered.
```
echo "88.191.101.8 packages.medibuntu.org" | sudo tee -a /etc/hosts
```

Now updates:KS

how do I mark thread as solved?

---

