---
title: "CD/DVD not supported?"
date: 2011-07-26
forum: General Help
---

### Post by El3mentGamer on 2011-07-26
Why not? Trying to burn an .iso file to a dvd, and i get this...

[IMG]http://i1211.photobucket.com/albums/cc434/El3mentGamer/Screenshot-1.png[/IMG]

Please help!

---

### Post by DawieS on 2011-07-26
The default 10.04 installation is not able to read or write DVD's, probably to avoid possible legal issues in some countries.
To be able to read DVD's, you have to install an additional repository and library. Open a terminal and type:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get -q update
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
sudo apt-get -q update
sudo aptitude install libdvdcss2
```

---

### Post by El3mentGamer on 2011-07-26
**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list**
[sudo] password for brandon: 
--2011-07-26 12:41:52--  [http://www.medibuntu.org/sources.list.d/natty.list](http://www.medibuntu.org/sources.list.d/natty.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org")... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80]("http://www.medibuntu.org%7C88.191.127.22%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 274 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 274         --.-K/s   in 0s      

2011-07-26 12:41:53 (2.75 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [274/274]

**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get -q update**
```
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty InRelease
Ign [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick InRelease
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty InRelease
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty InRelease
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security InRelease
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty InRelease
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty InRelease
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates InRelease
Get:1 [http://download.virtualbox.org]("http://download.virtualbox.org/") natty Release.gpg [197 B]
Get:2 [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty InRelease [7,092 B]
Hit [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick Release.gpg
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty InRelease
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release.gpg
Hit [http://archive.canonical.com]("http://archive.canonical.com/") natty Release.gpg
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release.gpg
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty Release.gpg
Get:3 [http://download.virtualbox.org]("http://download.virtualbox.org/") natty Release [5,393 B]
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty Release.gpg
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty Release
Hit [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick Release
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release
Hit [http://archive.canonical.com]("http://archive.canonical.com/") natty Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty/contrib i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates Release.gpg
Hit [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick/main i386 Packages
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Sources
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/free i386 Packages/DiffIndex
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty/contrib TranslationIndex
Hit [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty Release
Hit [http://download.virtualbox.org]("http://download.virtualbox.org/") natty/contrib i386 Packages
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main i386 Packages
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main TranslationIndex
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted i386 Packages
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty/main TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted TranslationIndex
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/non-free i386 Packages/DiffIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main i386 Packages
Ign [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick/main TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse TranslationIndex
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/free TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe TranslationIndex
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/non-free TranslationIndex
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty/contrib Translation-en_US
Ign [http://download.virtualbox.org]("http://download.virtualbox.org/") natty/contrib Translation-en
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/free i386 Packages
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en_US
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner Translation-en_US
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty/main Sources
  404  Not Found
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner Translation-en
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty/main i386 Packages
  404  Not Found
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/non-free i386 Packages
Ign [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick/main Translation-en_US
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty/main Translation-en_US
Ign [http://linux.dropbox.com]("http://linux.dropbox.com/") maverick/main Translation-en
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") natty/main Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/main Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty/universe Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") natty-updates/universe Translation-en
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/free Translation-en_US
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/free Translation-en
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") natty/non-free Translation-en
```Fetched 199 B in 26s (7 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[B]brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
[/B] Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get -q update**
[HTML]Ign http://download.virtualbox.org natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://extras.ubuntu.com natty InRelease
Ign http://linux.dropbox.com maverick InRelease
Ign http://security.ubuntu.com natty-security InRelease
Ign http://archive.canonical.com natty InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Get:1 http://download.virtualbox.org natty Release.gpg [197 B]
Get:2 http://packages.medibuntu.org natty InRelease [7,092 B]
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://packages.medibuntu.org natty InRelease
Ign http://ppa.launchpad.net natty Release.gpg
Hit http://extras.ubuntu.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release.gpg
Get:3 http://download.virtualbox.org natty Release [5,393 B]
Ign http://download.virtualbox.org natty Release
Hit http://archive.canonical.com natty Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://linux.dropbox.com maverick Release
Ign http://ppa.launchpad.net natty Release
Ign http://download.virtualbox.org natty/contrib i386 Packages/DiffIndex
Hit http://extras.ubuntu.com natty Release
Hit http://security.ubuntu.com natty-security Release
Hit http://archive.canonical.com natty Release
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://linux.dropbox.com maverick/main i386 Packages
Ign http://download.virtualbox.org natty/contrib TranslationIndex
Hit http://extras.ubuntu.com natty/main Sources
Hit http://security.ubuntu.com natty-security/main Sources
Ign http://packages.medibuntu.org natty/free i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com natty Release
Hit http://archive.canonical.com natty/partner i386 Packages
Hit http://download.virtualbox.org natty/contrib i386 Packages
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates Release
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Ign http://linux.dropbox.com maverick/main TranslationIndex
Ign http://packages.medibuntu.org natty/non-free i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://security.ubuntu.com natty-security/restricted Sources
Ign http://packages.medibuntu.org natty/free TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Ign http://download.virtualbox.org natty/contrib Translation-en_US
Ign http://packages.medibuntu.org natty/non-free TranslationIndex
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Ign http://download.virtualbox.org natty/contrib Translation-en
Hit http://packages.medibuntu.org natty/free i386 Packages
Ign http://extras.ubuntu.com natty/main Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en
Err http://ppa.launchpad.net natty/main Sources
  404  Not Found
Hit http://packages.medibuntu.org natty/non-free i386 Packages
Ign http://linux.dropbox.com maverick/main Translation-en_US
Err http://ppa.launchpad.net natty/main i386 Packages
  404  Not Found
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://linux.dropbox.com maverick/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en[/HTML]Fetched 199 B in 30s (7 B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo aptitude install libdvdcss2**
sudo: aptitude: command not found

---

### Post by seawolf167 on 2011-07-26
Questions:

[LIST]
[*]Is your burner capable of burning dvds?
[*]Have you inserted a blank dvd?
[*]Does the dvd burner work? (can you play dvds?)
[*]Is the disk inserted large enough?
[*]Do you have the following packages?
[/LIST]
```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by El3mentGamer on 2011-07-26
[B]This is what i got when trying those codes.

brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get install ubuntu-restricted-extras[/B]
[sudo] password for brandon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
 ubuntu-restricted-extras : Depends: ubuntu-restricted-addons but it is not going to be installed
                            Recommends: gstreamer0.10-plugins-ugly-multiverse but it is not going to be installed
                            Recommends: gstreamer0.10-plugins-bad-multiverse but it is not going to be installed
                            Recommends: libavcodec-extra-52 but it is not going to be installed
                            Recommends: libmp4v2-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get install libdvdread4**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.26-1natty1) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.26-1natty1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh**
--2011-07-26 14:15:41--  [http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages](http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7997 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-XJ7FOM/Packages'

100%[======================================>] 7,997       43.8K/s   in 0.2s    

2011-07-26 14:15:42 (43.8 KB/s) - `/tmp/dvdcss-XJ7FOM/Packages' saved [7997/7997]

--2011-07-26 14:15:42--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-XJ7FOM/libdvdcss.deb'

100%[======================================>] 38,036      21.9K/s   in 1.7s    

2011-07-26 14:15:45 (21.9 KB/s) - `/tmp/dvdcss-XJ7FOM/libdvdcss.deb' saved [38036/38036]

(Reading database ... 
dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 213709 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-XJ7FOM/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by seawolf167 on 2011-07-26
Please type this command

```
sudo apt-get -f install
```

post any errors, then run the three commands I previously posted.

When you copy/paste the output, put them inside CODE tags by clicking the hash mark when typing a reply.

---

### Post by El3mentGamer on 2011-07-26
Im getting a weird looking dialog box in the terminal that says "Package Configuration". it says <ok> at the bottom but i cant click it or type in anything. What to do?

---

### Post by leclerc65 on 2011-07-26
Use the Tab key.

---

### Post by El3mentGamer on 2011-07-26
I got this after typing in "sudo apt-get -f install" and clicking okay on the "package configuration"

```
brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get -f install
[sudo] password for brandon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  valac-0.10 compizconfig-settings-manager libhal1 libgluezilla libxdot4
  esound-clients
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 sun-java6-bin sun-java6-jre unixodbc
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
  libmyodbc odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed:
  gsfonts-x11 sun-java6-bin unixodbc
The following packages will be upgraded:
  sun-java6-jre
1 upgraded, 3 newly installed, 0 to remove and 92 not upgraded.
1 not fully installed or removed.
Need to get 36.5 MB/36.7 MB of archives.
After this operation, 105 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-bin i386 6.26-1natty1 [30.1 MB]
Get:2 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-jre all 6.26-1natty1 [6,371 kB]
Fetched 36.5 MB in 2min 51s (213 kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package unixodbc.
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 213709 files and directories currently installed.)
Unpacking unixodbc (from .../unixodbc_2.2.14p2-2ubuntu1_i386.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6.26-1natty1_i386.deb) ...
Preparing to replace sun-java6-jre 6.24-1build0.10.10.1 (using .../sun-java6-jre_6.26-1natty1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-jre ...
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.21_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Setting up unixodbc (2.2.14p2-2ubuntu1) ...
Setting up gsfonts-x11 (0.21) ...
Setting up sun-java6-jre (6.26-1natty1) ...
Setting up sun-java6-bin (6.26-1natty1) ...
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by El3mentGamer on 2011-07-26
Pressed <ok> and retryed the other codes.

```
 libavformat52 depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libhighgui2.1 depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter1 depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter1 depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter1 depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavfilter1 depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libmlt3 depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libavdevice52 depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (<< 5:0) | libavcodec-extra-52 (<< 5:0); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec52 (<< 5:0) | libavcodec-extra-52 (<< 5:0); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (>= 4:0.6.2-1ubuntu1) | libavcodec-extra-52 (>= 4:0.6.2); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 ffmpeg depends on libavcodec52 (<< 4:0.6.2-99) | libavcodec-extra-52 (<< 4:0.6.2-99); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
 libquicktime1 depends on libavcodec52 (>= 4:0.6-1~) | libavcodec-extra-52 (>= 4:0.6-1~); however:
  Package libavcodec52 is to be removed.
  Package libavcodec-extra-52 is not installed.
(Reading database ... 214735 files and directories currently installed.)
Removing libavcodec52 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libavcodec-extra-52.
(Reading database ... 214723 files and directories currently installed.)
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.6.2-1ubuntu2+medibuntu1_i386.deb) ...
Setting up libfaac0 (1.26-0.1ubuntu2) ...
Setting up libmp3lame0 (3.98.4-0ubuntu1) ...
Setting up libopenjpeg2 (1.3+dfsg-4) ...
Setting up libx264-106 (2:0.106.1741-3) ...
Setting up libxvidcore4 (2:1.2.2+debian-1ubuntu2) ...
Setting up libavcodec-extra-52 (4:0.6.2-1ubuntu2+medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package apport-hooks-medibuntu.
(Reading database ... 214735 files and directories currently installed.)
Unpacking apport-hooks-medibuntu (from .../apport-hooks-medibuntu_1medibuntu1_all.deb) ...
Selecting previously deselected package liboil0.3.
Unpacking liboil0.3 (from .../liboil0.3_0.3.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-fluendo-mp3.
Unpacking gstreamer0.10-fluendo-mp3 (from .../gstreamer0.10-fluendo-mp3_0.10.15.debian-1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-pitfdll.
Unpacking gstreamer0.10-pitfdll (from .../gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu2_i386.deb) ...
Selecting previously deselected package libmjpegtools-1.9.
Unpacking libmjpegtools-1.9 (from .../libmjpegtools-1.9_1%3a1.9.0-0.5ubuntu4_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad-multiverse.
Unpacking gstreamer0.10-plugins-bad-multiverse (from .../gstreamer0.10-plugins-bad-multiverse_0.10.21-1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly-multiverse.
Unpacking gstreamer0.10-plugins-ugly-multiverse (from .../gstreamer0.10-plugins-ugly-multiverse_0.10.17-1_i386.deb) ...
Selecting previously deselected package libmp4v2-0.
Unpacking libmp4v2-0 (from .../libmp4v2-0_1%3a1.6dfsg-0.2ubuntu9_i386.deb) ...
Selecting previously deselected package ubuntu-restricted-addons.
Unpacking ubuntu-restricted-addons (from .../ubuntu-restricted-addons_7_i386.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from .../ubuntu-restricted-extras_43_i386.deb) ...
Selecting previously deselected package w32codecs.
Unpacking w32codecs (from .../w32codecs_1%3a20110131-0.1medibuntu3_i386.deb) ...
Selecting previously deselected package icedtea-plugin.
Unpacking icedtea-plugin (from .../icedtea-plugin_1.1~20110420-0ubuntu1.1_i386.deb) ...
Selecting previously deselected package icedtea6-plugin.
Unpacking icedtea6-plugin (from .../icedtea6-plugin_6b21.1~20110420-0ubuntu1.1_i386.deb) ...
Setting up apport-hooks-medibuntu (1medibuntu1) ...
Setting up liboil0.3 (0.3.17-2ubuntu1) ...
Setting up gstreamer0.10-fluendo-mp3 (0.10.15.debian-1) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu2) ...
Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu4) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1) ...
Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.17-1) ...
Setting up libmp4v2-0 (1:1.6dfsg-0.2ubuntu9) ...
Setting up ubuntu-restricted-addons (7) ...
Setting up ubuntu-restricted-extras (43) ...
Setting up w32codecs (1:20110131-0.1medibuntu3) ...
Setting up icedtea-plugin (1.1~20110420-0ubuntu1.1) ...
Setting up icedtea6-plugin (6b21.1~20110420-0ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  valac-0.10 compizconfig-settings-manager libhal1 libgluezilla libxdot4
  esound-clients
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 92 not upgraded.
brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2011-07-26 15:09:58--  http://packages.medibuntu.org/dists/natty/free/binary-i386/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7997 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-lwECBj/Packages'

100%[======================================>] 7,997       40.8K/s   in 0.2s    

2011-07-26 15:09:59 (40.8 KB/s) - `/tmp/dvdcss-lwECBj/Packages' saved [7997/7997]

--2011-07-26 15:09:59--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-lwECBj/libdvdcss.deb'

100%[======================================>] 38,036      61.8K/s   in 0.6s    

2011-07-26 15:10:00 (61.8 KB/s) - `/tmp/dvdcss-lwECBj/libdvdcss.deb' saved [38036/38036]

(Reading database ... 215272 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-lwECBj/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list
--2011-07-26 15:11:03--  http://www.medibuntu.org/sources.list.d/natty.list
Resolving www.medibuntu.org... 88.191.127.22
Connecting to www.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 274 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 274         --.-K/s   in 0s      

2011-07-26 15:11:03 (5.86 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [274/274]
```

---

