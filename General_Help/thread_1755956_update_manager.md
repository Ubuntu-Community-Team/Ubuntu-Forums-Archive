---
title: "update manager"
date: 2011-05-11
forum: General Help
---

### Post by vin60 on 2011-05-11
Each time I use the update manager i get this error.           W:Failed to fetch [http://ubuntu.osuosl.org/ubuntu/dist...kports/Release]("http://ubuntu.osuosl.org/ubuntu/dists/natty-backports/Release")  Unable to find expected entry 'universedeb/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.                               
I have removed and reinstalled the update manager completely from the  synaptic package manager and many different servers and still the same.I  have also tried to update from the terminal.My network is up as I can  surf as usual.I am relatively new to Ubuntu.So any help would be  appreciated!  Thanks!

---

### Post by EmmGeeImage on 2011-05-11
In the command line, you can update the repositories by typing:

"  /etc/apt/sources.list    " without the quote marks.

Simply type that in, type in your password and watch it go to work.

Once you update, you should not see the messages of old repository list items being ignored.

---

### Post by plucky on 2011-05-12
> **vin60 said:**
> Each time I use the update manager i get this error.           W:Failed to fetch [http://ubuntu.osuosl.org/ubuntu/dist...kports/Release]("http://ubuntu.osuosl.org/ubuntu/dists/natty-backports/Release")  Unable to find expected entry 'universedeb/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.                               
I have removed and reinstalled the update manager completely from the  synaptic package manager and many different servers and still the same.I  have also tried to update from the terminal.My network is up as I can  surf as usual.I am relatively new to Ubuntu.So any help would be  appreciated!  Thanks!

Post your sources.list.

Open a terminal and ```
cat /etc/apt/sources.list
```


> EmmGeeImage 	
Re: update manager
In the command line, you can update the repositories by typing:

" /etc/apt/sources.list " without the quote marks.

Simply type that in, type in your password and watch it go to work.

That won't work.To update your sources.list you need to run ```
sudo apt-get update
```

Good Luck

---

### Post by vin60 on 2011-05-12
OK.Heres the source list. But I still get the same message when I try to update in the terminal.Does this mean that there no updates?



vince@vince-ThinkPad-T43:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty universe
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty multiverse
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-security main restricted
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-security universe
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-security multiverse
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-proposed restricted main multiverse universe
deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) natty-backports restricted main multiverse universedeb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib
vince@vince-ThinkPad-T43:~$

---

### Post by vin60 on 2011-05-12
I forget to mention that I have tried several different repository and I get the same result.Thanks for the quick responses!

---

### Post by plucky on 2011-05-12
> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner


You need to edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the two lines above.

This is the first time I have seen a sources.list with an IP address in place of a hostname.

Also I would remove the backports repository, as the backports updates can break your system.

Then run ```
sudo apt-get update
```

Good Luck

---

### Post by vin60 on 2011-05-14
Sorry for the delay with following up.I have tried all the suggestions and some I found on my own.Still the same issue.So I'm gonna do a fresh install and start over.Thanks for all your help [EmmGeeImage]("http://ubuntuforums.org/member.php?u=745117") and Plucky and for the fast responses.

---

### Post by vin60 on 2011-05-15
I just wanted to let everyone know how I solved my update manager woes.I took another look at my source list and found a backport I must have missed.And there also a line for virtualbox to download.I removed both and all is back to normal.So thanks again for all the wonderful Info.:guitar:

---

