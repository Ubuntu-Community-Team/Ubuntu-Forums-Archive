---
title: "Apt-get update does not work well"
date: 2010-05-20
forum: General Help
---

### Post by LebLinux on 2010-05-20
Hello,

I am on 10.04 and since yesterday I could manage to apt-get update without any problems.

Here is my sources.lst

> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid restricted main
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe


[B]Here is what apt-get update gives:
[/B]

>  sudo apt-get update
Get:1 [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
99% [1 Translation-en_US bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Get:2 [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
49% [2 Translation-en_US bzip2 0B] [Connecting to portal.aub.edu.lb] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:4 [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) lucid Release.gpg
73% [3 Translation-en_US bzip2 0B] [Waiting for headers] [Connecting to portal.aub.edu.lb]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:5 [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
75% [5 Translation-en_US bzip2 0B] [Connecting to portal.aub.edu.lb (10.11.12.13)] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:6 [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
54% [6 Translation-en_US bzip2 0B] [Connecting to lb.archive.ubuntu.com] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Get:8 [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) lucid Release
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) lucid Release

Get:9 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
54% [9 Translation-en_US bzip2 0B] [Connecting to portal.aub.edu.lb (10.11.12.13)]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:10 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
46% [10 Translation-en_US bzip2 0B] [Connecting to portal.aub.edu.lb (10.11.12.13)]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:11 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
40% [11 Translation-en_US bzip2 0B] [Connecting to security.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release

Fetched 84.1kB in 1s (49.3kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://lb.archive.ubuntu.com/ubuntu/dists/lucid/Release)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.


Regards,
Saad

---

### Post by Elie-M on 2010-05-20
hello fellow lebanese Comrad ;)

look as a primary step, I for one, would generate a new source list and replace the existing 1 and try to update. 


to generate a new one go to: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

pick ur system info and what packages u want and generate. take the output and put it in the place of old sources and try to update.

---

### Post by plucky on 2010-05-20
Have you tried changing your download server?

Sometimes the servers get out of sync.

**System > Administration > Software Sources** and on the first page select download from and select another server.

Or wait for a day for your server to sync up with the main server.

Good Luck

---

### Post by LebLinux on 2010-05-20
Thanks, I tried both way and still getting same results.

---

### Post by LebLinux on 2010-05-20
> Fetched 131kB in 4s (28.7kB/s)
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)


What would generate these errors?

---

### Post by unitydesktop on 2010-05-20
delete the repos that are not working and run apt-get update again. something wrong with the repos.

---

### Post by LebLinux on 2010-05-20
The thing is that they are all not working!

---

### Post by Elie-M on 2010-05-20
Edit: sry disregard this I missed ur earlier post

---

### Post by LebLinux on 2010-05-20
Elie I tired and generated a sources from your link and replaced it with my currently posted sources.list and I got the same problem. And now am back to my origianl sources.lst.

In synaptics its working fine. When I press reload.

---

### Post by Elie-M on 2010-05-20
one solution worked for me once is that I deleted the authentication keys located in source list in the menu bar. then I manually added the lucid keyz. cz it looks like the ubuntu cant use the keys provided to check signatures of the packages.

Edit: btw it looks like u're using the lebanese servers. Try what I told u and change the server to the main server.

---

### Post by LebLinux on 2010-05-20
could you provide me for lucid keys? lb

---

### Post by Elie-M on 2010-05-20
well not b4 1 hour, cz I'm at work and I use The lame windows on my work computer


use this:

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
(no chars row)
(no chars row)



and delete the keyz cz those doesnt need keys as far as I know, the generator didnt give any anyway.

---

### Post by LebLinux on 2010-05-20
Man I think there is something wrong with my  proxy connection. In synaptics things are going smooth and without any problem I get the updates reloaded. I am using proxy with credentials inside the preferences in Synaptic. 

But in Terminal when using apt-get update it does not work. Using export variable http_proxy. However to make sure my terminal is working thru proxy I did and recieved the following:

$ host us.archive.ubuntu.com
us.archive.ubuntu.com has address 91.189.88.46
us.archive.ubuntu.com has address 91.189.92.166
us.archive.ubuntu.com has address 91.189.88.30
us.archive.ubuntu.com has address 91.189.88.40
us.archive.ubuntu.com has address 91.189.88.45
=================================================

---

### Post by Elie-M on 2010-05-20
In the way I understood it, the last thing u said isnt that logical to me since both are using the same sources to get the updates... :S

anywayz as I understand ubuntu, aptitude and synaptic are 2 different packages, so it could be a bug in aptitude.. Did u delete the keys and click restore defaults?

my keys are 437D05B5 and FBB75451

BTW also try: 
sudo apt-get update && sudo apt-get upgrade


oh btw do u have VirtualBox Installed? there was some users that had the same problems if they had Vbox installed with some transparent proxy messing up aptitude


U can try this also:

in Synaptic, Preferences, under the Network tab, check to see whether  direct connection to the Internet is chosen. If not, select, apply and  see if that works

---

### Post by LebLinux on 2010-05-20
Yah I checked everything and still no go. The only way to update or to install is by using synaptic.

---

### Post by Armag3ddon on 2010-05-21
You should try first to clear your archive files you do that with

```
sudo apt-get clean
```

And then, try to update again

```
sudo apt-get update
```

if this doesn't work for you, try my source.list

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://lb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted main multiverse universe #Added by software-properties

## Added by Armageddon
# deb http://ppa.launchpad.net/network-manager/trunk/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu jaunty main
```

Ok, there are some useless lines you might want to comment for example

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://lb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse


```

I didn't have time to work on my source.list but so far it works for me...

and you might want to disregard these lines also, they are commented anyway.

```
## Added by Armageddon
# deb http://ppa.launchpad.net/network-manager/trunk/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu jaunty main
```

I was trying something out with those.

If this does not work, try to reinstall the keyrings of Lucid Lynx...

hopefully I'm not mistaken about this, and it's good you asked, it is called "ubuntu-keyring" I think this is what you are looking for, try to reinstall it...

---

### Post by klyndt on 2010-07-31
I had the same problem and as soon as I replaced my /etc/apt/sources.list file with the one provided by Armag3ddon, "apt-get update" finally worked. It hasn't worked since my Lucid upgrade. I compared my sources.list and Armag3ddon's with this result:

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties
[COLOR="DarkOrange"]Klyndt:[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties
[COLOR="DarkOrange"]Klyndt:[/COLOR]
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
[COLOR="DarkOrange"]Klyndt:[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
[COLOR="DarkOrange"]Klyndt:[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
[COLOR="DarkOrange"]Klyndt:[/COLOR]
[COLOR="Red"]#[/COLOR] deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
[COLOR="Red"]#[/COLOR] deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
[COLOR="DarkOrange"]Klyndt:[/COLOR]
[COLOR="Red"]#[/COLOR] deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
[COLOR="Red"]#[/COLOR] deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

[COLOR="DarkOrange"]Armag3ddon:[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports restricted main multiverse universe #Added by software-properties
[COLOR="DarkOrange"]Klyndt:[/COLOR]
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.cononical.com/](http://archive.cononical.com/) lucid partner

I hope this helps someone.
Klyndt

---

### Post by WanderingAlbatross on 2010-08-03
Thanks, Armag3ddon.  IT looks like it worked on ye olde laptop (Compaq 1200) running Xubuntu.

---

### Post by solarpenguin on 2010-11-19
Hi everyone.
  
 As well as  [my ongoing DVD Creator problems]("http://ubuntuforums.org/showthread.php?t=1620488"), I'm also having trouble with Update Manager, which keeps giving errors like this:

```
W: Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-2lucid1_i386.deb
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)


W: Failed to fetch http://packages.medibuntu.org/pool/non-free/m/mplayer/mplayer_1.0~rc3+svn20090426-1ubuntu16.1+medibuntu1_i386.deb
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
```I have had [trouble with upgrades before]("http://ubuntuforums.org/showthread.php?t=1574356"), which might have something to do with it.

Anyway, after looking through these threads, I've already  removed Google Chrome and tried changing the "mirror" in Software  Sources.  Unfortunately, trying to change the "mirror" just makes  Software  Sources give me these errors:

```
Failed to fetch http://ubuntu.datahop.net/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ubuntu.datahop.net:http' (-5 - No address associated with hostname)

Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-backports/Release.gpg  Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)

Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

Some index files failed to download, they have been ignored, or old ones used instead.

```  According to the thread, it seems the next step is to manually edit this "sources list" file but I'm having trouble actually doing that.  I did finally manage to find the file, after ages of searching from the Places menu.  (For any other newbies with the same problem: you have to start with Computer > File System, not the normal Home Folder.)  

But now I've found it, I can't edit it.  Double clicking just brings up the Software Sources program again, while right clicking and choosing Gedit won't let me change anything in it!  How can I get edit it properly?  I'm afraid I'm not much good at this technical stuff, as you've probably noticed, so I need clear, precise "click here, then click there" instructions.

Thanks if you can help.

---

### Post by solarpenguin on 2010-11-23
Bump

---

### Post by klyndt on 2010-12-09
You'll need to open a terminal window and navigate to the proper directory and then sudo gedit on the file.

```
cd /etc/apt/
sudo gedit sources.list

```

Enter your password and that should open gedit with the proper authority to change that file. Hope that helps.

---

### Post by uRock on 2010-12-09
Why not use the GUI? System> Administration> Software Sources in Lucid.

---

### Post by sikander3786 on 2010-12-09
@solarpenguin:

> Something wicked happened resolving 'ubuntu.datahop.net:http' (-5 - No address associated with hostname)


The error message quoted above suggests a problem with DNS resolution. I would suggest to switch to Google DNS for the time being and see if that gets resolved.

See Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

