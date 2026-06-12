---
title: "Synaptic Problem"
date: 2010-01-13
forum: General Help
---

### Post by frank cox on 2010-01-13
[COLOR=Red]**Solved!**[/COLOR]


Hi Everyone:

My synaptic gave error on line 51 of my /etc/apt/sources.list , I removed it , then on 44 and now on 29. 

This is the file. Any help you can give me will be appreciated. 

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
 repository.
 N.B. software from this repository may not have been tested as
extensively as that contained in the main release, although it includes
 ##newer versions of some applications which may provide useful features.

or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
## deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) r

---

### Post by john newbuntu on 2010-01-13
Did you make a copy of this before editing it?  If you did not, always make one in future.  I think you have a few line/s that begin with "NB".  Please put a comment "#" in front of it.
I am suspecting a similar problem with the line that says "or updates from the Ubuntu security team.". 
The last line should be:
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

You may have more errors,  If this doesn't work, I'd start with a clean sources.list from your liveCD and tweak the additions.  Even better use the system->admin->software sources.

---

### Post by Soul-Sing on 2010-01-13
> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04

A double one.

> You may have more errors, If this doesn't work, I'd start with a clean sources.list from your liveCD and tweak the additions. Even better use the system->admin->software sources.

+1 or get a default sources.list from one of us, i am not on jaunty
at the moment.

---

### Post by frank cox on 2010-01-13
Thanks-as soon as I did it I was kicking myself for not making a copy.
I think I will start from scratch with the fie from the CD.
Thanks

---

### Post by plucky on 2010-01-13
> **frank cox said:**
> Thanks-as soon as I did it I was kicking myself for not making a copy.
I think I will start from scratch with the fie from the CD.
Thanks

Or generate one from [here](http://repogen.simplylinux.ch/)


Good Luck

---

### Post by frank cox on 2010-01-14
> **plucky said:**
> Or generate one from [here]("http://repogen.simplylinux.ch/")


Good Luck

I made a new one and it did not work either. Here it is.
Thanks again!!!
Error
E: Type 'https://launchpad.net/netbook-remix' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



New List
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
#### Ubuntu Netbook Remix (Source) -
[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)
## Run this command: gpg --keyserver subkeys.pgp.net --recv B796B6FE
&& gpg --export --armor B796B6FE | sudo apt-key add -
deb-src [http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu) jaunty
main
#### VLC & X264 (Source) - [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2F021AC1
&& gpg --export --armor 2F021AC1 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
#### VLC Media Player (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys
40130828 && gpg --export -a 40130828 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) jaunty main
#### Wine (Source) - [http://www.winehq.org/](http://www.winehq.org/)
## Run this command: wget -q
[http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add
-
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main
#### X Updates (Source) -
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv AF1CDFA9
&& gpg --export --armor AF1CDFA9 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty
main
#### XBMC Media Center (Source) - [http://xbmc.org/](http://xbmc.org/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 91E7EE5E
&& gpg --export --armor 91E7EE5E | sudo apt-key add -
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main

---

### Post by frank cox on 2010-01-14
This is bizarre-I edited the line and now the file comes up empty and when I try to repaste the edited file is says it can't find it when I try to save.

Your help is appreciated!

---

### Post by frank cox on 2010-01-14
This is a pain, now it brings up a blank page and says this  when you try to close it


Could not find the file /home/forrest/etc/apt/sources.list.

---

### Post by plucky on 2010-01-14
> **frank cox said:**
> This is a pain, now it brings up a blank page and says this  when you try to close it


Could not find the file /home/forrest/etc/apt/sources.list.

You have to be in **sudo** mode to edit the sources.list file.You are trying to edit a file in your /home folder.

From a terminal window (**Applications > Accessories > Terminal**)
```
gksudo gedit /etc/apt/sources.list
```


> I made a new one and it did not work either. Here it is.
Thanks again!!!
Error
E: Type 'https://launchpad.net/netbook-remix' is not known on line 3 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



New List
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
#### Ubuntu Netbook Remix (Source) -
[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)
## Run this command: gpg --keyserver subkeys.pgp.net --recv B796B6FE
&& gpg --export --armor B796B6FE | sudo apt-key add -
deb-src [http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ppa/ubuntu) jaunty
main
#### VLC & X264 (Source) - [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 2F021AC1
&& gpg --export --armor 2F021AC1 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
#### VLC Media Player (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: gpg --keyserver keyserver.ubuntu.com --recv-keys
40130828 && gpg --export -a 40130828 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) jaunty main
#### Wine (Source) - [http://www.winehq.org/](http://www.winehq.org/)
## Run this command: wget -q
[http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add
-
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main
#### X Updates (Source) -
[https://launchpad.net/~ubuntu-x-swat...ive/x-updates/](https://launchpad.net/~ubuntu-x-swat...ive/x-updates/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv AF1CDFA9
&& gpg --export --armor AF1CDFA9 | sudo apt-key add -
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty
main
#### XBMC Media Center (Source) - [http://xbmc.org/](http://xbmc.org/)
## Run this command: gpg --keyserver subkeys.pgp.net --recv 91E7EE5E
&& gpg --export --armor 91E7EE5E | sudo apt-key add -
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main 


Those are all warning messages that you have not added authentication keys for those repositories.

Do you need those PPAs'?

See [here](https://help.launchpad.net/Packaging/PPA/InstallingSoftware) on how to add a PPA with key.

Or you can run the commands that the warnings are showing to add the keys.For example ```
gpg --keyserver subkeys.pgp.net --recv 91E7EE5E && gpg --export --armor 91E7EE5E | sudo apt-key add -
```

Good Luck

p.s I have added a basic Jaunty sources.list as a text attachment.

---

### Post by frank cox on 2010-01-15
I know you have to be in root, I guess I was too tired to mess with it. I will try again when I actually sleep more than 3 hours. Thanks everyone. I will let you know how it came out.

---

### Post by frank cox on 2010-01-20
Thanks I finally got everything working with my software sources thanks to you.
More importantly I know how to fix it and understand the errors thanks to you.

---

