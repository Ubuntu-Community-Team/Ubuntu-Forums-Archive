---
title: "problem with apt-get update"
date: 2006-03-24
forum: General Help
---

### Post by harys on 2006-03-24
hi, i have configured my network using :


cd /etc/network

nano interfaces

iface eth0 inet dhcp

i have configured the proxy doing :


cd /etc
nano bash.bashrc

export http_proxy=http://proxy.studenti.unicatt.it:80/

export ftp_proxy=http://proxy.studenti.unicatt.it:80/
(ctrl-x and y >return key)

i loaded the proxy and network with :


ifup eth0

bash /etc/bash.bashrc
and i got this message in the console :
root@harys:/etc# ifup eth0
ifup: interface eth0 already configured
root@harys:/etc# bash /etc/bash.bashrc
/etc/bash.bashrc: line 7: return: can only `return' from a function or sourced script
root@harys:/etc# ping -c 5 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.93.104) 56(84) bytes of data.
From 10.10.113.254 icmp_seq=1 Packet filtered
From 10.10.113.254 icmp_seq=3 Packet filtered

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 0 received, +2 errors, 100% packet loss, time 4001ms

i tried to configure apt with "cd /etc/apt" that is now my "nano sources.list" look for now : 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main $

## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main universe multiverse restri$ deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main universe multiverse re$
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted univ$# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted $
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
at last i used the command apt-get update and i get this error and i don't know how to do yet :
root@harys:/# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33), connection timed out
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Could not connect to proxy.unicatt.it:8080 (10.1.1.33). - connect (113 No route to host)
Reading package lists... Done
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

thanks so much for any help.
harys

---

### Post by Blunts on 2006-03-25
Can we say bad proxy?

---

