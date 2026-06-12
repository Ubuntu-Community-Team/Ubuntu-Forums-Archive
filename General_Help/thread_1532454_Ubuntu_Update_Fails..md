---
title: "Ubuntu Update Fails."
date: 2010-07-16
forum: General Help
---

### Post by justincase_2008 on 2010-07-16
I went to do a system update today and got a error message saying it could get info for Edgy... Some how update manager got switched to Edgy and i cant figure out how to get it to go back to Lucid. Under software sources on the other software  Ubuntu 6.10 'Edgy Eft' is there instead of Lucid. I didnt do any changes to the system at all i just got a pop up say updates are availble so i click update like always and BAM error.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404  Not Found [IP:]
Some index files failed to download, they have been ignored, or old ones used instead.

How can i get Lucid back instead of this Edgy crap.

---

### Post by snowpine on 2010-07-16
Welcome to the forums! Support for Edgy ended April 2008.

You can download and install the current release, 10.04 from here: [http://www.ubuntu.com/](http://www.ubuntu.com/)

Good luck! :)

---

### Post by justincase_2008 on 2010-07-16
> **snowpine said:**
> Welcome to the forums! Support for Edgy ended April 2008.

You can download and install the current release, 10.04 from here: [http://www.ubuntu.com/](http://www.ubuntu.com/)

Good luck! :)

I have 10.04 thats the thing that is killing me. I dont know how the hell it switched.[ATTACH]163634[/ATTACH][ATTACH]163635[/ATTACH]

---

### Post by snowpine on 2010-07-16
Have you tried unchecking the little box next to where it says "Ubuntu 6.10 Edgy Eft"? :)

---

### Post by justincase_2008 on 2010-07-16
> **snowpine said:**
> Have you tried unchecking the little box next to where it says "Ubuntu 6.10 Edgy Eft"? :)

Yup when i do i get a pop up saying 

The information about available software is out-of-date.

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

I reload, it dls 71 files and cant get it to update just keeps dling the same 71 files over and over.

The Edgy stays there and wont switch back to Lucid like it should be.

From what i think, i would need that Luicd check to be there instead of Edgy so i can update luicd

---

### Post by snowpine on 2010-07-16
Please go to Applications, Accessories, Terminal. Type the following command, then copy & paste the results back here, using "code" blocks to make it easier to read.

The command is: 

```
cat /etc/apt/sources.list
```

To make it appear in a code box like that I typed:

```
(code)cat /etc/apt/sources.list(/code)
```

except instead of parenthesis () I used square brackets [ ] :)

---

### Post by justincase_2008 on 2010-07-16
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
# deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse

```

---

### Post by snowpine on 2010-07-16
Do you see these two lines?

```
# deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main
```

You added them for some reason, maybe you were following an outdated tutorial for installing wine?

We can edit this file as "root" using "sudo" (actually we use "gksu" because gedit is a graphical application). Be very careful! From the terminal again:

```
gksu gedit /etc/apt/sources.list
```

Delete those two lines, save the file, quit the text editor, and try your update again.

ps Nice job with the "code" tags. ;)

---

### Post by justincase_2008 on 2010-07-16
How in the world did that get added lol. And thanks first time posting on the forum since its been the first time i could figure out how to fix it. Thanks for helpin me out.

---

### Post by snowpine on 2010-07-16
You are very welcome. :) And for future reference, Wine is already part of the Ubuntu repositories, so installing it is as easy as:

```
sudo apt-get install wine
```

Or of course you could use the Ubuntu Software Center if you prefer a GUI interface. :)

---

### Post by justincase_2008 on 2010-07-16
> **snowpine said:**
> You are very welcome. :) And for future reference, Wine is already part of the Ubuntu repositories, so installing it is as easy as:

```
sudo apt-get install wine
```

Or of course you could use the Ubuntu Software Center if you prefer a GUI interface. :)

thats the command i used. very very strange to me.

---

### Post by snowpine on 2010-07-16
> **justincase_2008 said:**
> thats the command i used. very very strange to me.

You're right; my bad. :) Try this first:

```
sudo apt-get update
```

That will "refresh" your software sources. Until you do that, it will still be trying to download from the Edgy repo. :(

---

### Post by justincase_2008 on 2010-07-16
I ran that right after i wrote my reply seems to be working, ill see the next time a update becomes available

---

### Post by snowpine on 2010-07-16
Excellent news, I hope you have many more positive experiences with Ubuntu Forums!
:)

---

