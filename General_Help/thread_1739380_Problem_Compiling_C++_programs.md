---
title: "Problem Compiling C++ programs"
date: 2011-04-25
forum: General Help
---

### Post by ssn2009 on 2011-04-25
I'm having problems compiling C++ programs. I've tried compiling C++ programs with extension .cc and .cpp. I've tried compiling with gcc, g++ and even cc (with .cc extension files). 

Earlier (as g++ wasn't installed) i tried installing g++ (sudo apt-get install g++) for which i got the message "g++ has no installation candidate". Later from Synaptic i found it as g++-2.95 and installed it. I've also installed pentium-builder

Whenever i've tried to install "build-essential" (using apt-get and aptitude) i've got messages along the line of "no installation candidate". I've searched many posts and not got the answer for this. I've treid update and upgrade before installation, no use. I have all the repositories checked in software sources and the server as "main server". 

Now, the main problem is: (when trying to compile a .cpp file)
user@dell-desktop:~$ g++ hello.cpp
Unable to exec g++.real: No such file or directory

user@dell-desktop:~$ gcc hello.cpp
gcc.real: error trying to exec 'cc1plus': execvp: No such file or directory

user@dell-desktop:~$ cc hello.cpp
gcc.real: error trying to exec 'cc1plus': execvp: No such file or directory


(I have ubuntu Intrepid Ibex)

---

### Post by Sirkyuubi on 2011-04-25
use synaptic to install build essential

Post any errors you get aswell

---

### Post by ssn2009 on 2011-04-26
Sorry if this is a rather dumb question, but how exactly do you find build essential in synaptic? 

If you give quick search with "build essential", you get multiple results (the not installed ones) starting with:
sbuild, polyxmass-common, gap-libs, gnome-core, kdrill etc. How do you know which are the corresponding packages?

The already installed ones (from the same search) are: system-services, startup-tasks, gnome-panel, python-minimal, python2.5-minimal, perl-base etc.

---

### Post by idoitprone on 2011-04-26
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

you cant be as stupid as me. I have to reinstall an os 3 times in one day lol.

if you want to be lazy run this in the terminal 

```
sudo apt-get install build-essential checkinstall
```

---

### Post by mc4man on 2011-04-26
> (I have ubuntu Intrepid Ibex)
Ibex is well past end of life, did you adjust your sources to reflect that (to the old-releases source entries

Could be something like this (though I've never had reason to do so
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```

or here is a slightly different layout (uses gutsy, you're intrepid
[http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/)

---

### Post by ssn2009 on 2011-04-27
> **idoitprone said:**
> [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

you cant be as stupid as me. I have to reinstall an os 3 times in one day lol.

if you want to be lazy run this in the terminal 

```
sudo apt-get install build-essential checkinstall
```


I got this: 

user@dell-desktop:~$ sudo apt-get install build-essential checkinstall
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

---

### Post by ssn2009 on 2011-04-27
> **mc4man said:**
> Ibex is well past end of life, did you adjust your sources to reflect that (to the old-releases source entries

Could be something like this (though I've never had reason to do so
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```or here is a slightly different layout (uses gutsy, you're intrepid
[http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/)

bash: deb: command not found

---

### Post by SkyNet2029 on 2011-04-27
build-essential should be pulled in from module-assistant

so,

```
sudo apt-get install module-assistant
```
then
```
m-a update
```
select prepare from menu and let it pull in the required libraries.
You should be able to compile after that.

---

### Post by ssn2009 on 2011-04-29
> **SkyNet2029 said:**
> build-essential should be pulled in from module-assistant

so,

```
sudo apt-get install module-assistant
```then
```
m-a update
```select prepare from menu and let it pull in the required libraries.
You should be able to compile after that.


After "install module-assistant" and "m-a update" i got the warning: "/user/src/compat-wireless-1.0-4.9 seems to contain unconfigured kernel source!" (module-assistant error message).

After selecting ok: 
  	 	 	 	 	the same warning message, this time with linux-headers 2.6.27-10

After clicking ok for that:
the same warning message, this time with linux-headers 2.6.27-7

After clicking ok for that: 
"You are not root and no replacement directory (the -u option) is specified. Unable to continue."

The installation of module-assistant went without problems. Can you also tell me exactly what I am doing with these commands?

---

### Post by mc4man on 2011-04-29
> **ssn2009 said:**
> bash: deb: command not found
You need to edit your /etc/apt/sources.list, not run in a terminal
The old intrepid sources don't exist anymore, that's why you get all these type messages
> Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
[COLOR="Red"]is only available from another source[/COLOR]
E: Package build-essential has no installation candidate 

[U]
Note to anyone helping the OP - he is running 8.10 (intrepid[/U]

---

### Post by ssn2009 on 2011-05-01
> **mc4man said:**
> You need to edit your /etc/apt/sources.list, not run in a terminal
The old intrepid sources don't exist anymore, that's why you get all these type messages

[U]
Note to anyone helping the OP - he is running 8.10 (intrepid[/U]
What changes do i have to make to sources.list?

---

### Post by ssn2009 on 2011-05-11
> **mc4man said:**
> Ibex is well past end of life, did you adjust your sources to reflect that (to the old-releases source entries

Could be something like this (though I've never had reason to do so
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```or here is a slightly different layout (uses gutsy, you're intrepid
[http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of]("http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/")[-ubuntu/]("http://soniahamilton.wordpress.com/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/")

I'm totally new to this. My sources.list is as follows: 

## deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) intrepid main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

I would like to know what changes i've to make to it?

---

