---
title: "update problems"
date: 2009-11-26
forum: General Help
---

### Post by modustollens on 2009-11-26
I installed 9.10.  When I tried to do the update it crashed and locked up the machine; I had to turn the power off and run fsck.

When up and running again I tried the update.

But now it says there is an error in one of the lines of the sources.list.

When I try to open it using gedit it says that it cannot understand the character coding and hence cannot display the contents.  

I opened the package manager; unchecked the sources; reverted; then checked again and reverted; but the same problem occured:

E: Line 1 too long in source list /etc/apt/sources.list.
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


And trying to open the sources.list gives this error:

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.


Being a noob I am not sure what to do at this point:

I suppose if I could find another sources.list and copy it over to overwrite my erroneous unreadable one?  But where would I get that?

Any suggestions?

Thanks

MT

---

### Post by Soul-Sing on 2009-11-26
What code are you using to open the sources.list? It should not open a .bin file! (or try to open a .bin)

---

### Post by jacobs444 on 2009-11-26
try nano instead of gedit, if this does nothing, then something got corrupted

---

### Post by modustollens on 2009-11-26
Thanks for the help lads: here I what I have done...


The code I was using with gedit was:

sudo gedit /etc/apt/sources.list



I tried using nano;  I used this command

sudo gedit /etc/apt/sources.list

Here is the output of the nano command:

^B^E&#65533;@"^A       &#65533;&#65533;^AB^@^@^B&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^G^B^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^$


I have looked at and edited the sources.list before in my older installations - and I know its not supposed to look like this.  Hence it appears that it has been corrupted.  Moreover the update manage and the software source application does not seem to be able to correct the corruption.

Suggestions?


Here is what I plan to do: reload the live cd; and copy the sources.list from the live cd to my hd and see what I can accomplish with that...

MT

---

### Post by akakingess on 2009-11-26
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://76.73.4.58/ubuntu/ karmic main restricted
deb-src http://76.73.4.58/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://76.73.4.58/ubuntu/ karmic-updates main restricted
deb-src http://76.73.4.58/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://76.73.4.58/ubuntu/ karmic universe
deb-src http://76.73.4.58/ubuntu/ karmic universe
deb http://76.73.4.58/ubuntu/ karmic-updates universe
deb-src http://76.73.4.58/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://76.73.4.58/ubuntu/ karmic multiverse
deb-src http://76.73.4.58/ubuntu/ karmic multiverse
deb http://76.73.4.58/ubuntu/ karmic-updates multiverse
deb-src http://76.73.4.58/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://76.73.4.58/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://76.73.4.58/ubuntu/ karmic-security main restricted
deb-src http://76.73.4.58/ubuntu/ karmic-security main restricted
deb http://76.73.4.58/ubuntu/ karmic-security universe
deb-src http://76.73.4.58/ubuntu/ karmic-security universe
deb http://76.73.4.58/ubuntu/ karmic-security multiverse
deb http://76.73.4.58/ubuntu/ karmic-proposed restricted main multiverse universe
deb-src http://76.73.4.58/ubuntu/ karmic-security multiverse
```

That is not code, but a copy of my sources.list, if you want to start there.  Just copy and paste into a new file and save it as /etc/apt/sources.list.  Hope this helps you get started.

---

### Post by modustollens on 2009-11-26
Sweet; thanks - it will save me from having to load up the live cd session and recover the file...


I copied it over; and the update appears to be working too; so, whatever original error there was in my sources.list was not to found in yours....  However both times during the update failure it was the samba software update that caused the update manager and the entire OS to crash...


Thanks again...

---

