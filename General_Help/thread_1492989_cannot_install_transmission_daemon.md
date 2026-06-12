---
title: "cannot install transmission daemon"
date: 2010-05-25
forum: General Help
---

### Post by goodvikings on 2010-05-25
Hi all

I have a headless server that i'm trying to install the web ui of transmission onto. After much search of the internet, I still cannot get the first step.

(lets assume all commands as su)

I'm supposed to apt-get install transmission-daemon with the result:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package transmission-daemon
```

If I then do aptitude search transmission it comes back with

```
p   transmission
p   transmission-cli
p   transmission-common
c   transmission-gtk
```

I would assume that by installing transmission, it would install the daemon, but then the next steps in the installation aren't available.

Any ideas?

Damian

---

### Post by andru183 on 2010-05-25
i know nothing of this matter but i did i quick search and this result seems to answer your question

[http://www.vanutsteen.nl/2008/12/09/installing-transmission-daemon-on-ubuntu/](http://www.vanutsteen.nl/2008/12/09/installing-transmission-daemon-on-ubuntu/)

---

### Post by goodvikings on 2010-05-25
All of the ways I've tried to install this, none of them generate the settings.jsob file that is needed. I've tried starting the daemon and stopping it as a few had recommended, but to no avail.

Failing that, can anyone recommend a easy to install torrent client with a web ui for a headless server?

---

### Post by geirha on 2010-05-26
What release is this, and what version of transmission is in the repositories?

```
lsb_release -a
aptitude show transmission
```

---

### Post by goodvikings on 2010-05-26
> **geirha said:**
> What release is this, and what version of transmission is in the repositories?

```
lsb_release -a
aptitude show transmission
```

The release is 8.04 Hardy

The second command gives:
```
Package: transmission
State: not installed
Version: 1.06-0ubuntu6.1
Priority: optional
Section: universe/net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 20.5k
Depends: transmission-cli (>= 1.06-0ubuntu6.1), transmission-common (= 1.06-0ubuntu6.1),
         transmission-gtk (>= 1.06-0ubuntu6.1)
Description: free, lightweight BitTorrent client
 Transmission is a simple BitTorrent client. It features a very simple, intuitive interface
 (gui and command-line) on top on an efficient, cross-platform back-end.

 This package installs both CLI and GUI versions of transmission.
Homepage: http://www.transmissionbt.com/

```

I can't help but notice that the transmission-daemon isn't in the dependancies.

---

### Post by geirha on 2010-05-26
Oh, that's an ancient version of Transmission. I think transmission-daemon was in the transmission-cli package in those days. I'd recommend either upgrading from Ubuntu 8.04 LTS to Ubuntu 10.04 LTS, or grab the latest version of transmission-daemon from the PPA at [https://edge.launchpad.net/~transmissionbt/+archive/ppa?field.series_filter=hardy](https://edge.launchpad.net/~transmissionbt/+archive/ppa?field.series_filter=hardy)

---

### Post by goodvikings on 2010-05-26
Cheers man that got it working

---

