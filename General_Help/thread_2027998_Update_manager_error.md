---
title: "Update manager error"
date: 2012-07-17
forum: General Help
---

### Post by rapattack1 on 2012-07-17
Hi the Update manager alerted me i needed updates and i ran it but i get what is in the attached image. I looked at the repositories and i can see the entry for dl.google.com but i don't remember what that is and if i installed it. Can anyone enlighten me please ?

---

### Post by raja.genupula on 2012-07-17
post the output of ```
cat /etc/apt/sources.list
```

there must be some errors at the lines ,at reported lines  in the error image . 

after correcting them try to update again , If is there any problem with the corrections post it here , we will make corrections and we will reply you back .

---

### Post by rapattack1 on 2012-07-17
```
cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Ailurus - http://code.google.com/p/ailurus/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9A6FE242
deb http://ppa.launchpad.net/ailurus/ppa/ubuntu lucid main

#### AWN (Avant Window Navigator) Testing Packages - http://awn-project.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv BF810CD5 && gpg --export --armor BF810CD5 | sudo apt-key add -
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu lucid main

#### Banshee - https://edge.launchpad.net/~banshee-team
## Run this command: gpg --keyserver subkeys.pgp.net --recv 6E80C6B7 && gpg --export --armor 6E80C6B7  | sudo apt-key add -
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu lucid main

#### Blueman - https://edge.launchpad.net/~blueman/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 951DC1E2
deb http://ppa.launchpad.net/blueman/ppa/ubuntu lucid main

#### Breathe Icon Set - https://edge.launchpad.net/~breathe-dev/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 45FFBBBA
deb http://ppa.launchpad.net/breathe-dev/ppa/ubuntu lucid main

#### Cairo Dock - http://www.glx-dock.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu lucid main

#### Conky - https://launchpad.net/conky
## Run this command: gpg --keyserver subkeys.pgp.net --recv 95628707 && gpg --export --armor 95628707 | sudo apt-key add -
deb http://ppa.launchpad.net/norsetto/ppa/ubuntu lucid main

#### Deluge BitTorrent - http://www.deluge-torrent.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 249AD24C && gpg --export --armor 249AD24C  | sudo apt-key add -
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main

#### Emesene - http://www.emesene.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu lucid main

#### Esmska - http://code.google.com/p/esmska/ 
## Run this command: wget -q -O - http://repo.palatinus.cz/repo.key | sudo apt-key add -
# deb http://repo.palatinus.cz/stable /

#### Exaile - http://www.exaile.org
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 43CBFCC0
deb http://ppa.launchpad.net/exaile-devel/ubuntu lucid main

#### FreeNX  - http://freenx.berlios.de/
## Run this command: gpg --keyserver subkeys.pgp.net --recv D018A4CE && gpg --export --armor D018A4CE | sudo apt-key add -
deb http://ppa.launchpad.net/freenx-team/ppa/ubuntu lucid main

#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free

#### Google Linux Software Repositories (testing) - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
deb http://dl.google.com/linux/deb/ testing non-free

#### KMess - http://kmess.org/
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1D2EC123
deb http://ppa.launchpad.net/kmess-packages/kmess-stable/ubuntu lucid main

#### Kubuntu Backports - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main

#### Kubuntu Experimental - https://launchpad.net/~kubuntu-ppa/+archive/experimental
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu karmic main

#### Kubuntu Updates - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main

#### LMMS - Linux MultiMedia Studio - http://lmms.sourceforge.net
## Run this command: gpg --keyserver subkeys.pgp.net --recv ADDE29B2 && gpg --export --armor ADDE29B2 | sudo apt-key add -
deb http://ppa.launchpad.net/tobydox/ppa/ubuntu lucid main

#### MediaInfo - http://mediainfo.sourceforge.net
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu lucid main

#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ lucid free non-free

#### Miro HD Video Player - http://www.getmiro.com/
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu jaunty/

#### OpenOffice.org 3.0 - https://launchpad.net/~openoffice-pkgs/+archive
## Run this command: gpg --keyserver subkeys.pgp.net --recv 247D1CFF && gpg --export --armor 247D1CFF  | sudo apt-key add -
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu lucid main

#### OpenShot - http://www.openshotvideo.com
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu lucid main

#### Pidgin - http://pidgin.im
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8   
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main

#### Playdeb - http://www.playdeb.net/
## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu jaunty-getdeb games

#### PlayOnLinux - http://www.playonlinux.com
## Run this command: sudo apt-get update && sudo apt-get install playonlinux
deb http://deb.playonlinux.com/ lucid main

#### Remastersys
deb http://www.geekconnection.org/remastersys/repository karmic/

#### Skype - http://www.skype.com
## Run this command: gpg --keyserver pgp.mit.edu --recv-keys 0xd66b746e && gpg --export --armor 0xd66b746e  | sudo apt-key add -
deb http://download.skype.com/linux/repos/debian/ stable non-free

#### SMPlayer - http://smplayer.sourceforge.net/
## Run this command: gpg --keyserver subkeys.pgp.net --recv A58BCAE3 && gpg --export --armor A58BCAE3  | sudo apt-key add -
deb http://ppa.launchpad.net/rvm/ppa/ubuntu lucid main

#### Terminator - http://www.tenshu.net/terminator/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu lucid main

#### Themes for GNOME and Ubuntu - https://edge.launchpad.net/~bisigi/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu lucid main

#### Tor: anonymity online - http://www.torproject.org/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 94C09C7F && gpg --export --armor 94C09C7F  | sudo apt-key add -
deb http://deb.torproject.org/torproject.org lucid main

#### Ubuntu Tweak - http://ubuntu-tweak.com/
## Run this command: gpg --keyserver subkeys.pgp.net --recv 0624A220 && gpg --export --armor 0624A220  | sudo apt-key add -
deb http://ppa.launchpad.net/tualatrix/ubuntu lucid main

#### VirtualBox - http://www.virtualbox.org
## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free

#### VLC Media Player  - http://www.videolan.org/vlc/
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys 40130828 && gpg --export -a 40130828 | sudo apt-key add -
deb http://ppa.launchpad.net/c-korn/ppa/ubuntu lucid main

#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: gpg --keyserver subkeys.pgp.net --recv AF1CDFA9 && gpg --export --armor AF1CDFA9  | sudo apt-key add -
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main
deb http://www.bchemnet.com/suldr/ debian extra

```

---

### Post by rapattack1 on 2012-07-18
Hi any suggestions?

---

### Post by dino99 on 2012-07-18
> **rapattack1 said:**
> Hi any suggestions?

is that makes sense to you ?

## UNOFFICIAL  REPOS ##

note: ubuntu suppose you know what you are doing. And you are mixing Lucid with Karmic :(

---

### Post by rapattack1 on 2012-07-18
No i have no idea what you mean. I am not that experienced with Linux yet. I do know you are suggesting somehow i have two distros together or something. I don't know how that is possible so have no clue and didn't even notice that in the repository

---

### Post by plucky on 2012-07-18
> **rapattack1 said:**
> No i have no idea what you mean. I am not that experienced with Linux yet. I do know you are suggesting somehow i have two distros together or something. I don't know how that is possible so have no clue and didn't even notice that in the repository

Why have you added all those third party repositories?


> #### Playdeb - [http://www.playdeb.net/](http://www.playdeb.net/)
## Run this command: wget -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) jaunty-getdeb games


That is for Jaunty.


> #### Kubuntu Updates - [https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa](https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) karmic main


That is for Karmic.

Are you following someone's advice or Howto?

---

### Post by rapattack1 on 2012-07-19
I don't know what that is...i don't know how to be more clear. I may have followed advice here on this forum in the past but i don't remember specifically anything that you are showing me

---

### Post by claracc on 2012-07-19
The answer is clear, you have to remove all the ppa's not corresponding to lucid lynx.

As dino99 and plucky have addressed:

> deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) jaunty-getdeb games 

> deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) karmic main 

> ## UNOFFICIAL REPOS ##[QUOTE]you are mixing Lucid with Karmic [/QUOTE]

---

### Post by rapattack1 on 2012-07-20
OK i removed the two you mentioned but there are more in the repositories that are for the other distros. Do i remove them too? I got this after i did a reload after i removed the two you mentioned...sorry i couldn't understand the other persons post so i didn't know what to do

---

### Post by rapattack1 on 2012-07-23
Haven't had that error thing happen again so do i need to remove the other things? thanks :0)

---

### Post by claracc on 2012-07-24
> OK i removed the two you mentioned but there are more in the repositories that are for the other distros. Do i remove them too? 

Yes, you remove all ppas not corresponding to ubuntu lucid lynx.

---

### Post by rapattack1 on 2012-07-24
OK did so and i still got this:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages.gz)  404  Not Found [IP: 74.125.237.100 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by claracc on 2012-07-24
What for you have this ppa [http://dl.google.com/linux/deb/dists/in](http://dl.google.com/linux/deb/dists/in) the sources.list?

> Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release) Unable to find expected entry non-free/binary-i386/Packages in Meta-index file (malformed Release file?)
 Failed to fetch [http://dl.google.com/linux/deb/dists...86/Packages.gz](http://dl.google.com/linux/deb/dists...86/Packages.gz) 404 Not Found [IP: 74.125.237.100 80]

This two lines day to you that the packages are not in the addresses, mo more. If you don't need this ppa or you don't know why you added, better remove it.

---

### Post by rapattack1 on 2012-07-24
OK will remove then as i have no idea what it is for. OK didn't get that error so all looks good. Just doing an update/upgrade now and will report back later :0)

---

### Post by rapattack1 on 2012-07-26
Well things seem to be ok now but will give it a few days to see

---

### Post by ranger1021994 on 2012-07-26
> **rapattack1 said:**
> OK i removed the two you mentioned but there are more in the repositories that are for the other distros. Do i remove them too? I got this after i did a reload after i removed the two you mentioned...sorry i couldn't understand the other persons post so i didn't know what to do

Remove repositories containing "Karmic" and "Jaunty".
Wherever you see Karmic or Jaunty in your repository,Remove the whole line.

---

### Post by rapattack1 on 2012-07-26
Yep did that...it was just that google line was the last baffling thing that really caused that error :0) it seems anyway

---

