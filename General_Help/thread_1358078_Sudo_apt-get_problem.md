---
title: "Sudo apt-get problem"
date: 2009-12-17
forum: General Help
---

### Post by Anonymous1 on 2009-12-17
Greetings,
I am using Ubuntu 9.10 karmic  
And having some trouble with sudo apt-get  
everytime I run it connection times out.
here is what happens :
:~$ sudo apt-get install php5-cli

 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a tork-data kdelibs-data liblualib50 tsocks binutils-static snmp
  libgdchart-gd2-noxpm liblua50 privoxy geoip-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear php5-suhosin
The following NEW packages will be installed:
  php5-cli php5-common
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
Need to get 2,931kB of archives.
After this operation, 6,193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  php5-common php5-cli
Install these packages without verification [y/N]? y
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) karmic-updates/main php5-common 5.2.10.dfsg.1-2ubuntu6.3
  Could not connect to 210.194.98.66:8080 (210.194.98.66), connection timed out
0% [Connecting to 210.194.98.66 (210.194.98.66)

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb)  Unable to connect to 210.194.98.66 8080:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This happens with any application not just this one.

The second part of my problem is with Ubuntu software center ,any software I try to install stops at 5%.

 help would be appreciated.

---

### Post by nibirumarduk on 2009-12-17
> **Anonymous1 said:**
> Greetings,
I am using Ubuntu 9.10 karmic  
And having some trouble with sudo apt-get  
everytime I run it connection times out.
here is what happens :
:~$ sudo apt-get install php5-cli

 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a tork-data kdelibs-data liblualib50 tsocks binutils-static snmp
  libgdchart-gd2-noxpm liblua50 privoxy geoip-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear php5-suhosin
The following NEW packages will be installed:
  php5-cli php5-common
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
Need to get 2,931kB of archives.
After this operation, 6,193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  php5-common php5-cli
Install these packages without verification [y/N]? y
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) karmic-updates/main php5-common 5.2.10.dfsg.1-2ubuntu6.3
  Could not connect to 210.194.98.66:8080 (210.194.98.66), connection timed out
0% [Connecting to 210.194.98.66 (210.194.98.66)

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb)  Unable to connect to 210.194.98.66 8080:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This happens with any application not just this one.

The second part of my problem is with Ubuntu software center ,any software I try to install stops at 5%.

 help would be appreciated.

Most probably a transient network issues. Have you tried switching to a different mirror e.g. [http://de.archive.ubuntu.com/](http://de.archive.ubuntu.com/), [http://fr.archive.ubuntu.com/](http://fr.archive.ubuntu.com/) or [http://mirrors.kernel.org/](http://mirrors.kernel.org/) ? And then re-run sudo aptitude update && sudo aptitude safe-upgrade

Best of luck!

---

### Post by running_rabbit07 on 2009-12-17
I tried the link that failed and it starts the download for the .deb that your system is trying to fetch. I would recommend running the two commands that are right below the failed to fetch line at the bottom.

[http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb) Works in Firefox.

---

### Post by running_rabbit07 on 2009-12-17
> **nibirumarduk said:**
> Most probably a transient network issues. Have you tried switching to a different mirror e.g. [http://de.archive.ubuntu.com/](http://de.archive.ubuntu.com/), [http://fr.archive.ubuntu.com/](http://fr.archive.ubuntu.com/) or [http://mirrors.kernel.org/](http://mirrors.kernel.org/) ? And then re-run sudo aptitude update && sudo aptitude safe-upgrade

Best of luck!

Could you share how to make those changes to the sources.list? I think to get there it is ```
gksudo gedit /etc/apt/sources.list
``` but I do not know exactly which lines to tell the OP to change there.

---

### Post by running_rabbit07 on 2009-12-17
Anonomous1, what country are you in?

---

### Post by running_rabbit07 on 2009-12-18
I am thinking it is the red line that may need to be changed to make this work.```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
[COLOR=Red]deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted[/COLOR]
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
```

---

### Post by nibirumarduk on 2009-12-18
> **running_rabbit07 said:**
> Could you share how to make those changes to the sources.list? I think to get there it is ```
gksudo gedit /etc/apt/sources.list
``` but I do not know exactly which lines to tell the OP to change there.

Yeah, to effect the changes, you need to fire up an editor (e.g. graphical ones such as gedit or a text one like vim), open the file /etc/apt/sources.list, change all references from [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) to e.g. [http://mirrors.kernel.org/](http://mirrors.kernel.org/) . 

Like this:
```
deb http://mirrors.kernel.org/ubuntu/ karmic main restricted universe multiverse
deb http://mirrors.kernel.org/ubuntu/ karmic-updates main restricted universe multiverse
deb http://mirrors.kernel.org/ubuntu/ karmic-security main restricted universe multiverse
deb http://mirrors.kernel.org/ubuntu/ karmic-backports main restricted universe multiverse
deb http://mirrors.kernel.org/ubuntu/ karmic-proposed restricted main multiverse universe
```

While not that it matters much, **do disable the deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse** line also. Otherwise you may get apt or aptitude telling you of a duplicate entry since you now already have
deb [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/) karmic-security main restricted universe multiverse

And oh, **do remember to re-run sudo apt-get update && sudo apt-get upgrade** after you have save the changes. Although honestly, I recommend using aptitude over apt.

Best of luck!

---

### Post by eugeneross on 2009-12-18
The information provided was really very useful. Thanks very much for this lovely post.

---

### Post by PaulReaver on 2009-12-18
Because Ubuntu is aimed at desktop users I thought this might be helpful.  (don't flame, I've been a gentoo user for years)



Instead of manually changing sources.list,  you could change your sources.list this way:

System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the fastest for you.

---

### Post by running_rabbit07 on 2009-12-18
> **PaulReaver said:**
> Because Ubuntu is aimed at desktop users I thought this might be helpful.  (don't flame, I've been a gentoo user for years)



Instead of manually changing sources.list,  you could change your sources.list this way:

System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the fastest for you.

Here is a screen shot of that function. Good idea. I have been caught up on seeing the texts lately. Thanks for throwing that in.

---

### Post by nibirumarduk on 2009-12-18
> **PaulReaver said:**
> Because Ubuntu is aimed at desktop users I thought this might be helpful.  (don't flame, I've been a gentoo user for years)



Instead of manually changing sources.list,  you could change your sources.list this way:

System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the fastest for you.

Yes. Beneficial to know and will work most times especially for those using the desktop edition but there ain't such a feature for those on the server edition. Certain situations e.g. a botched grub or X upgrade resulting in failure to boot into the desktop compounded by a mirror network problem will leave you with but little choice to venture into the commandline world and edit the sources.list file via a cli text editor like nano, vim, emacs, etc. Thing is, at least you still have this choice of the cli and recovering from there. This ain't an option in certain other OSes. Especially if one mixes his/her repos such as official ones with ppas and others, tracking things like X, nvidia, kernel while not actively encourage, people are people, and people will use them despite the advise. 

Forget not the maxim, that it is human to err and that the trouble with people is that they don't learn from history and keeps on repeating the same old mistakes. Also that of "I'm different, immune, invincible or sort of, it'll never ever happen to me". So do we then turn around and laugh at them, tell them "serve you right" or should we help them? If we still want to help them, why don't we do so early? Can't speak for the rest but I prefer teaching the man how to fish rather than just give him the fish. Thus it is always advisable to learn the cli just in case. You never know when the need may occur. And if and when it does, and you don't know, it is natural of you the typical user to blame the distro and its users for not preparing you. This is but a very human quality.

---

### Post by bkmfs on 2009-12-18
----

---

### Post by Anonymous1 on 2009-12-22
> **Anonymous1 said:**
> Greetings,
I am using Ubuntu 9.10 karmic  
And having some trouble with sudo apt-get  
everytime I run it connection times out.
here is what happens :
:~$ sudo apt-get install php5-cli

 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a tork-data kdelibs-data liblualib50 tsocks binutils-static snmp
  libgdchart-gd2-noxpm liblua50 privoxy geoip-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  php5-common
Suggested packages:
  php-pear php5-suhosin
The following NEW packages will be installed:
  php5-cli php5-common
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
Need to get 2,931kB of archives.
After this operation, 6,193kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  php5-common php5-cli
Install these packages without verification [y/N]? y
Err [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) karmic-updates/main php5-common 5.2.10.dfsg.1-2ubuntu6.3
  Could not connect to 210.194.98.66:8080 (210.194.98.66), connection timed out
0% [Connecting to 210.194.98.66 (210.194.98.66)

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb)  Unable to connect to 210.194.98.66 8080:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This happens with any application not just this one.

The second part of my problem is with Ubuntu software center ,any software I try to install stops at 5%.

 help would be appreciated.


I modified the sources list and still the problem is not solved.   :(

---

### Post by Anonymous1 on 2009-12-22
> **bkmfs said:**
> You might have a half installed package gumming up your gears and this might take care of it:

dpkg -r -a


I tried that as well  .  still does not fix it.

---

### Post by Anonymous1 on 2009-12-22
> **PaulReaver said:**
> Because Ubuntu is aimed at desktop users I thought this might be helpful.  (don't flame, I've been a gentoo user for years)



Instead of manually changing sources.list,  you could change your sources.list this way:

System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the fastest for you.


Tried that as well ,the result is:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 210.194.98.66 8080:


root@anonymous:/home/anonymous# sudo killall aptitude
aptitude: no process found
root@anonymous:/home/anonymous# sudo killall aptitude



I just discovered  that most terminal based actions that require internet are n0t working.

For example ;

using sqlmap gives the folowing:
[07:07:18] [INFO] testing connection to the target url
[07:07:48] [WARNING] unable to connect to the target url or proxy, sqlmap is going to retry the request
[07:08:19] [WARNING] unable to connect to the target url or proxy, sqlmap is going to retry the request
[07:08:50] [WARNING] unable to connect to the target url or proxy, sqlmap is going to retry the request
[07:09:21] [ERROR] unable to connect to the target url or proxy.

Also btw  Ubuntu software center stops at 5% no matter what the software is

---

### Post by Anonymous1 on 2009-12-22
> **running_rabbit07 said:**
> I tried the link that failed and it starts the download for the .deb that your system is trying to fetch. I would recommend running the two commands that are right below the failed to fetch line at the bottom.

[http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.10.dfsg.1-2ubuntu6.3_i386.deb) Works in Firefox.

 it works from firefox ,prolly something wrong with terminal?

---

