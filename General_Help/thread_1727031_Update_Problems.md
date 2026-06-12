---
title: "Update Problems"
date: 2011-04-12
forum: General Help
---

### Post by youbob1212 on 2011-04-12
Ok for those who don't know me, This is what I'll say about my self. 

I'm running Ubuntu 10.10 64bit.. ok so while I was trying to get some other software to run(blender 2.56a) This little red triangle appeared on my top right hand corner. And I click on it in the attempt to get rid of it. 

So I tried one of the main options; that was to update software... and I get this little error message... 

> W:Failed to fetch [http://ppa.launchpad.net/cheleb/Spring/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/cheleb/Spring/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cheleb/Spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/Spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cheleb/povray-svn/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/cheleb/povray-svn/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cheleb/povray-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/povray-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

what can I do about this little problem:-k

Sorry for the lack of charter in this post. I'm very sleepy, do to the lack of sleep.. I know the solution  will be found out some how in the morning, However, not because of any sudden idea that has been running away from me, due the past few hours (this is because I'm a total Noob in Ubuntu), but maybe due to the kindness of others on this forum... 

Anyways, thank you of your time... 

P.S Trust me when I say this. When ever I do go to forum asking for help, that's because google failed me or I failed it... Well Goodnight every one. ):P

---

### Post by earthpigg on 2011-04-12
whatever project ppa.launchpad.net/cheleb/ is, they seem to have taken it down. so, lets remove the ppa.

back up your sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
```

edit your sources.list

```
sudo gedit /etc/apt/sources.list
```

find the ppa.launchpad.net/cheleb entries, and comment them out by putting a # in front of those lines.

save changes, quit gedit.
```

sudo apt-get update
```

---

### Post by youbob1212 on 2011-04-12
It's not there! 
> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

So what next

---

### Post by earthpigg on 2011-04-12
```
grep ppa.launchpad.net/cheleb /etc/apt/sources.list.d/*
```

show output, please.

---

### Post by youbob1212 on 2011-04-12
[HTML]/etc/apt/sources.list.d/cheleb-blender-svn-maverick.list:deb http://ppa.launchpad.net/cheleb/blender-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-blender-svn-maverick.list:deb-src http://ppa.launchpad.net/cheleb/blender-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-blender-svn-maverick.list.save:deb http://ppa.launchpad.net/cheleb/blender-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-blender-svn-maverick.list.save:deb-src http://ppa.launchpad.net/cheleb/blender-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-povray-svn-maverick.list:deb http://ppa.launchpad.net/cheleb/povray-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-povray-svn-maverick.list:deb-src http://ppa.launchpad.net/cheleb/povray-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-povray-svn-maverick.list.save:deb http://ppa.launchpad.net/cheleb/povray-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-povray-svn-maverick.list.save:deb-src http://ppa.launchpad.net/cheleb/povray-svn/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-spring-maverick.list:deb http://ppa.launchpad.net/cheleb/spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-spring-maverick.list:deb-src http://ppa.launchpad.net/cheleb/spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-Spring-maverick.list:deb http://ppa.launchpad.net/cheleb/Spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-Spring-maverick.list:deb-src http://ppa.launchpad.net/cheleb/Spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-spring-maverick.list.save:deb http://ppa.launchpad.net/cheleb/spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-spring-maverick.list.save:deb-src http://ppa.launchpad.net/cheleb/spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-Spring-maverick.list.save:deb http://ppa.launchpad.net/cheleb/Spring/ubuntu maverick main
/etc/apt/sources.list.d/cheleb-Spring-maverick.list.save:deb-src http://ppa.launchpad.net/cheleb/Spring/ubuntu maverick main
[/HTML]

go you go!

---

### Post by youbob1212 on 2011-04-12
bump. 
any help?:-({|=

---

### Post by earthpigg on 2011-04-12
I was sleeping, didn't mean to make you feel like i left you hanging :)


well, it looks like *some* of that repository has been taken down or moved to a new URL.

we can see this by comparing what we get from clicking on these two links (don't actually save or download it, just note that one offers to let you, and one returns 404 not found):

taken down: [http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)
not taken down: [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)

hopefully, the project's website documented this and the maintainer didn't simply go AWOL.

can you point me to the website that provided instructions to add those ppas? hopefully, it was from the official website of the project, not some random person's blog or similar. and, hopefully, they documented a migration path from their old PPA URLs to the new PPA URLs.

failing that, we will simply have to remove all of those entries and call the project dead...

EDIT: if you just want to remove those entries and be done with that project...

```
gksu nautilus
```

navigate to /etc/apt/sources.list.d

delete everything that starts with 'cheleb'.

close nautilus, ctrl+c in the terminal window.

```
sudo apt-get update
```

---

### Post by youbob1212 on 2011-04-12
> **earthpigg said:**
> I was sleeping, didn't mean to make you feel like i left you hanging :)


well, it looks like *some* of that repository has been taken down or moved to a new URL.

we can see this by comparing what we get from clicking on these two links (don't actually save or download it, just note that one offers to let you, and one returns 404 not found):

taken down: [http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/spring/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)
not taken down: [http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/cheleb/blender-svn/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)

hopefully, the project's website documented this and the maintainer didn't simply go AWOL.

can you point me to the website that provided instructions to add those ppas? hopefully, it was from the official website of the project, not some random person's blog or similar. and, hopefully, they documented a migration path from their old PPA URLs to the new PPA URLs.

failing that, we will simply have to remove all of those entries and call the project dead...

EDIT: if you just want to remove those entries and be done with that project...

```
gksu nautilus
```navigate to /etc/apt/sources.list.d

delete everything that starts with 'cheleb'.

close nautilus, ctrl+c in the terminal window.

```
sudo apt-get update
```

WOOT THAT DID THE TRICK!!! 

LOL the next time you go out of your way to help someone you better think twice about sleeping :P LOL Just kidding.

Hey man you helped me a lot. 

one final question, I'm a noob to ubuntu, is there an all in one resource or book that teaches you how to use this OS? because it's not easy sometimes getting around this OS. But BETS WINDOW :o.. 
Thanks again and cheers

---

### Post by earthpigg on 2011-04-13
glad i could help. i could have told you how to do that and be done with that project from your first post, but i wasn't sure that is what you wanted. be as clear as possible about your goals, and others can help you more efficiently. 

> **youbob1212 said:**
> one final question, I'm a noob to ubuntu, is there an all in one resource or book that teaches you how to use this OS? because it's not easy sometimes getting around this OS. But BETS WINDOW :o.. 
Thanks again and cheers

google and ubuntuforums.org and wikipedia is all i've ever used. [this]("http://ubuntu-manual.org/") exists, but i cannot vouch for its quality.

---

