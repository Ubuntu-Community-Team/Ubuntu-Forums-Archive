---
title: "Error with Adept: cannot commit changes-problem with synaptic install"
date: 2006-05-11
forum: General Help
---

### Post by jude254 on 2006-05-11
I have a problem with adept, whenever I click on commit changes after choosing to install a package,I get an error message:

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

I have for this reason tried to install synaptic first from adept, then from terminal giving these commands:

sudo apt-get install synaptic
it doesnt install because I have dependencies problems

dpkg -i namefile.deb
again doesnt install it because of dependencies problems

Do you have any suggestions?

I just need to get synaptic, because adept is giving me too many problems, and I believe that when I get to install synaptic, everything will be much easier!

any help is appreciated
thanks

---

### Post by Al3xanR0 on 2006-05-11
Have you tried```
apt-get update
``` then ```
apt-get install syanptic
```?

---

### Post by jude254 on 2006-05-11
Yes but I cannot install it thru terminal because it gives me dependencies problems

---

### Post by tonyr on 2006-05-11
Let's get some basic information first.  
Are you running Breezy or Dapper?
Show the terminal commands and actual error messages when the installs fail.

I used to get the problem messages in **adept** several versions
ago.  At that point I would exit **adept**, got to a terminal and do two things:
```

sudo dpkg --configure -a
sudo apt-get install -f

```

My current version of adept is 1.92ubuntu1.  Is that the version you have? I haven't
seen the problem in quite a while now.

---

### Post by jude254 on 2006-05-12
IM running Breezy 5.10-

I have tried sudo apt-get install -f and it removed synaptic. I dont know if that was suppsed to happen. Ill try edit my sources.list, cause I think that's at the root of the problems, and then do those two commands again, and see what happens. If I get error messages Ill post them here.

Thanks for now!

Ill get back to you

---

### Post by jude254 on 2006-05-17
Ok this is what I did:

Opened up a terminal and enter as root user, with su + password.

Then I configured apt-get for proxy connection, according to my proxy server:

root@kubuntuElisa:/home/elisa# export http_proxy=http://192.168.1.2:6588
root@kubuntuElisa:/home/elisa# export ftp_proxy=http://192.168.1.2:21

Then I did those two things you told me to do and this is what I got:

1) root@kubuntuElisa:/home/elisa# sudo dpkg --configure -a
then I pressed enter
2) root@kubuntuElisa:/home/elisa# sudo apt-get install -f
then pressed enter and got this script:
Lettura della lista dei pacchetti in corso... Fatto(reading packages....done)
Generazione dell'albero delle dipendenze in corso... Fatto (generating dependencies...done)
0 aggiornati, 0 installati, 0 da rimuovere e 249 non aggiornati.
(o upgraded, 0 installed, o to remove, and 248 not upgraded)
W: Impossibile controllare la lista dei pacchetti sorgente (impossible to control the list of source packages) [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-latest_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages (/var/lib/apt/lists/cipherfunk.org_pub_packages_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_amarok-latest_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
(its suggested to do apt-get update to correct these problems)

When I do apt-get update this is what I get:

Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:2 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:3 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg [307B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Get:5 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:6 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Get:7 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27,0kB]
Get:9 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release [11,0kB]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:10 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Get:11 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release [649B]
Get:12 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates Release [30,9kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release.gpg
Get:13 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports Release [19,6kB]
Get:14 [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release.gpg [309B]
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
  404 Not Found
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Get:15 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas/all Packages [19,3kB]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Sources
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Sources
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Sources
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [60,2kB]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Get:17 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Packages [39,0kB]
Get:18 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages [1786B]
Get:19 [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release [11,0kB]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Get:20 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:21 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/main Sources [18,6kB]
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Get:22 [http://people.ubuntu.com](http://people.ubuntu.com) ./ Sources [974B]
Get:23 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:24 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Packages [12,9kB]
Ign [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Get:25 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Packages [708B]
Get:26 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/universe Sources [1343B]
Get:27 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-updates/multiverse Sources [365B]
Get:28 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Packages [14,0kB]
Get:29 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:30 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Packages [26,1kB]
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Packages
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17,3kB]
Get:33 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:34 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35,0kB]
Get:37 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Get:38 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/universe Sources [10,2kB]
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Get:39 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Hit [http://pkg-boinc.alioth.debian.org](http://pkg-boinc.alioth.debian.org) breezy/universe Sources
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3830B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas Release
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [1025B]
Get:43 [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas/all Sources [6335B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
99 % (waiting for headers)

And it stops t 99 per cent.

My sources.list is:

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) breezy main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) breezy main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) breezy main

# Bleeding edge wine packages (packages)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Bleeding edge wine packages (sources)
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

# Osmo Salomas CVS amule packages (packages, GPG key: 70188C3B)
deb [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy/

# Osmo Salomas CVS amule packages (sources, GPG key: 70188C3B)
deb-src [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy/

# The Opera browser (packages)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# The Boinc! engine (packages)
deb [http://pkg-boinc.alioth.debian.org/ubuntu/](http://pkg-boinc.alioth.debian.org/ubuntu/) breezy universe

# The Boinc! engine (sources)
deb-src [http://pkg-boinc.alioth.debian.org/ubuntu/](http://pkg-boinc.alioth.debian.org/ubuntu/) breezy universe

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src [http://people.ubuntu.com/~jbailey/snapshot/bzr](http://people.ubuntu.com/~jbailey/snapshot/bzr) ./

Anyone can help???Please, I dont know what to do, and if I dont get to solve these problems I might have to return to windows:(

Thanks in advance
Elisa

---

### Post by Dpdk on 2006-09-25
Im having a problem a bit like this. Im running dapper and I have both Adept and Synaptic installed. Adept gives me the same error message (that there was a problem committing the changes. Synaptic tells me:

The package libdivxencore0-binary needs to be reinstalled, but I can't find an archive for it.

what do i need to do?

---

