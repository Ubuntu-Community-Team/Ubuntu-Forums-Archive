---
title: "sudo apt-get update errors..."
date: 2009-12-31
forum: General Help
---

### Post by switch10 on 2009-12-31
I have been getting errors with update lately...
```
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F7D0E1722382D57E
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24C
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E43D207C62D38753
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61260473F9D8BC54
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

```

there was a few more, but I deleted them in sources.list.  I was wondering about the Medibuntu source mostly.  I want to make sure it works.  Here is my sources.list

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Universal Applets
## 
deb http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.04/ ./

#### Abiword - http://www.abisource.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
deb http://ppa.launchpad.net/abiword-stable/ubuntu karmic main

#### AWN (Avant Window Navigator) Testing Packages - http://awn-project.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv BF810CD5 && gpg --export --armor BF810CD5 | sudo apt-key add -
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ubuntu karmic main

#### Blueman - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb http://ppa.launchpad.net/blueman/ppa/ubuntu karmic main

#### Cairo Dock - http://www.cairo-dock.org/ww_page.php?p=Accueil&#9001;=en
## Run this command: wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -

#### Chromium Project - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#### Deluge BitTorrent - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu karmic main

#### GNOME-Colors PPA - https://edge.launchpad.net/~gnome-colors-packagers/+archive/ppa
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2d79f61be8d31a30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

#### Gnome-Do - http://do.davebsd.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 77558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -

#### HandBrake - http://handbrake.fr/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 62D38753
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu karmic main

#### MediaInfo - http://mediainfo.sourceforge.net
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu karmic main

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
# deb http://packages.medibuntu.org/ karmic free non-free

#### Miro HD Video Player - http://www.getmiro.com/
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu karmic main

#### Wine - http://www.winehq.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main


####### 3rd Party Source Repos

#### Chromium Project (Source) - http://code.google.com/chromium/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 4E5E17B5 && gpg --export --armor 4E5E17B5 | sudo apt-key add -
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#### Deluge BitTorrent (Source) - http://www.deluge-torrent.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu karmic main

#### GNOME-Colors PPA (Source) - https://edge.launchpad.net/~gnome-colors-packagers/+archive/ppa
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2d79f61be8d31a30
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

#### Gnome-Do (Source) - http://do.davebsd.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 77558DD0
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#### MediaInfo (Source) - http://mediainfo.sourceforge.net
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu karmic main

#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src http://packages.medibuntu.org/ karmic free non-free

#### Themes for GNOME and Ubuntu (Source) - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

#### Ubuntu Tweak (Source) - http://ubuntu-tweak.com/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#### VLC Media Player  (Source) - http://www.videolan.org/vlc/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src http://ppa.launchpad.net/c-korn/ppa/ubuntu karmic main

#### Wine (Source) - http://www.winehq.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main

#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main

#### webcam support for empathy
# deb http://ppa.launchpad.net/telepathy/ubuntu karmic main

#### Dropbox
deb http://linux.getdropbox.com/ubuntu karmic main
deb-src http://linux.getdropbox.com/ubuntu karmic main


#### Program to make background picture stacks
deb http://ppa.launchpad.net/ruben-verweij/wallpaper-stacks/ubuntu lucid main
```

Thanks for the help :)

Dave

---

### Post by Mahngiel on 2009-12-31
Google search for GPG error is missing Pubkey. Check this link

[http://en.kioskea.net/faq/sujet-809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/sujet-809-debian-apt-get-no-pubkey-gpg-error)

---

### Post by MelDJ on 2009-12-31
try the link in my sig

---

### Post by switch10 on 2009-12-31
is this line causing the lines after it??
```
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

because I dont know the package source names on the other lines...

---

### Post by switch10 on 2009-12-31
Ok, so the Medibuntu source isnt giving me anymore problems, but how do I fix the other ones???

---

### Post by plucky on 2009-12-31
> **switch10 said:**
> Ok, so the Medibuntu source isnt giving me anymore problems, but how do I fix the other ones???

The answer is in the output of your sources.list for each entry.

e.g```
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E

```

Open a terminal window and copy and paste each of the commands. 

If you run each command for each of the PPA repositories,this will add the GPG key and the warnings will disappear.

Do you have a reason for adding all those repositories or are you using a script to add those repositories?

---

### Post by switch10 on 2009-12-31
> **plucky said:**
> The answer is in the output of your sources.list for each entry.

e.g```
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E

```

Open a terminal window and copy and paste each of the commands. 

If you run each command for each of the PPA repositories,this will add the GPG key and the warnings will disappear.

Do you have a reason for adding all those repositories or are you using a script to add those repositories?

I never really knew which ones I should add in the "official ubuntu repo's" section..  should I remove some??

thanks for the replies by the way..  I have been ignoring this problem for way to long :)

---

### Post by plucky on 2009-12-31
> I never really knew which ones I should add in the "official ubuntu repo's" section.. should I remove some??



Unless you have the specific software installed for each PPA archive,it would probably be better to un-tick the box in the "third Party" section of the "Software Sources" GUI,in which case the GPG key will no longer be required.

The PPA's are useful if you need the most up-to-date versions of the different software packages,which don't get updated between releases,but do get security fixes.It is up to you to decide what your requirements are.

Good Luck

---

### Post by switch10 on 2009-12-31
Thanks.  Yeah I use all that 3rd party software...  Thanks though, I have it pretty much sorted.

---

### Post by drs305 on 2009-12-31
Take a deep breath, then:

```

gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783  F7D0E1722382D57E  7D2C7A23BF810CD5  4874D3686E80C6B7  6B15AB91951DC1E2  5A9BF3BB4E5E17B5  C5E6A5ED249AD24C  2D79F61BE8D31A30  28A8205077558DD0  E43D207C62D38753  61260473F9D8BC54  6E871C4A881574DE  6AF0E1940624A220  71346C8340130828  5A9A06AEF9CB8DB0  3B22AB97AF1CDFA9 && gpg --export --armor 2EBC26B60C5A2783  F7D0E1722382D57E  7D2C7A23BF810CD5  4874D3686E80C6B7  6B15AB91951DC1E2  5A9BF3BB4E5E17B5  C5E6A5ED249AD24C  2D79F61BE8D31A30  28A8205077558DD0  E43D207C62D38753  61260473F9D8BC54  6E871C4A881574DE  6AF0E1940624A220  71346C8340130828  5A9A06AEF9CB8DB0  3B22AB97AF1CDFA9 | sudo apt-key add - 

```

Edit: Apparently too late.

---

### Post by switch10 on 2009-12-31
> **drs305 said:**
> Take a deep breath, then:

```

gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783  F7D0E1722382D57E  7D2C7A23BF810CD5  4874D3686E80C6B7  6B15AB91951DC1E2  5A9BF3BB4E5E17B5  C5E6A5ED249AD24C  2D79F61BE8D31A30  28A8205077558DD0  E43D207C62D38753  61260473F9D8BC54  6E871C4A881574DE  6AF0E1940624A220  71346C8340130828  5A9A06AEF9CB8DB0  3B22AB97AF1CDFA9 && gpg --export --armor 2EBC26B60C5A2783  F7D0E1722382D57E  7D2C7A23BF810CD5  4874D3686E80C6B7  6B15AB91951DC1E2  5A9BF3BB4E5E17B5  C5E6A5ED249AD24C  2D79F61BE8D31A30  28A8205077558DD0  E43D207C62D38753  61260473F9D8BC54  6E871C4A881574DE  6AF0E1940624A220  71346C8340130828  5A9A06AEF9CB8DB0  3B22AB97AF1CDFA9 | sudo apt-key add - 

```

Edit: Apparently too late.

Thanks!!!  
I was actually having trouble with two of them, this worked perfectly!  thanks a lot!  I will have to remember this one.

---

