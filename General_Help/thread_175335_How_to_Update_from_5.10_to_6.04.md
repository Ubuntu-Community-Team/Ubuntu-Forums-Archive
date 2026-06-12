---
title: "How to Update from 5.10 to 6.04"
date: 2006-05-13
forum: General Help
---

### Post by drayan69 on 2006-05-13
View coming next version of ubuntu i.e.6.04 will I have to install afresh or I can upgrade from 5.10 to 6.04 without disturbing my existing installation?

If upgradation is possible, please someone guide me step by step how to do it?

thanks

---

### Post by Ramses de Norre on 2006-05-13
sudo gedit /etc/apt/sources.list
change every "breezy" into "dapper"
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by 3rdalbum on 2006-05-13
Upgrading is not only possible, it's also a supported procedure.

First, open the file "/etc/apt/sources.list":
```

sudo nano /etc/apt/sources.list

```

Wherever it says "breezy" in the file, change it to "dapper" (except for the "deb cdrom:" line at the very top, unless you have a Dapper install CD that is)

Quit Nano by typing Control-X, and save the changes back to the same file. Now type:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

Installation will commence. You can even perform those steps now to upgrade to Dapper Flight 7, if you don't mind living adjacent to the edge.

EDIT: I was beaten by 3 minutes :-)

---

### Post by Quirky on 2006-05-13
Changing sources.list manually is no longer the preferred method. According to the wiki [https://wiki.ubuntu.com/DapperFlight7](https://wiki.ubuntu.com/DapperFlight7) the method you should use is simply:
```
gksudo "update-manager -d"
```
(assuming you have the latest Breezy update-manager.)

---

### Post by bluenova on 2006-05-13
> The "-d" switch instructs Update Manager to consider pre-release versions, including this Beta release. Without this switch, only official, final releases will be considered.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system. 
So this should mean when 6.04 goes stable that 5.10 will be automatically updated?

---

### Post by drayan69 on 2006-05-13
THANKS ALL 4 REPLIES

Subsequent to my switchover from windows, I settled for ubuntu after much handons on fedora and mandrake, suse etc.

ubuntu is rock solid, faster and I have no problems except sudo does not work..I am satisfied with ubuntu and now I am totally dependant on it. So I do not wish to disturb the installation during upgrade process. My problem is that my connectivity speed is only 64 kbps and I have a download limit of 150 Mb per day. 

Can online updation be done with this speed and limit?

Can shipit CDs be used to upgrade? I mean will during installation boot ubuntu 6.04 CD will automatically sense the 5.10 installation and upgrade it without disturbing data and all?

---

### Post by confused57 on 2006-05-13
[QUOTE=drayan69]

Can shipit CDs be used to upgrade? I mean will during installation boot ubuntu 6.04 CD will automatically sense the 5.10 installation and upgrade it without disturbing data and all?[/QUOTE]

I found this link that may help:

[http://www.ubuntuforums.org/showthread.php?t=157746&highlight=upgrade+breezy](http://www.ubuntuforums.org/showthread.php?t=157746&highlight=upgrade+breezy)

---

### Post by Hoffmann on 2006-05-13
[QUOTE=3rdalbum]Upgrading is not only possible, it's also a supported procedure.

First, open the file "/etc/apt/sources.list":
```

sudo nano /etc/apt/sources.list

```

Wherever it says "breezy" in the file, change it to "dapper" (except for the "deb cdrom:" line at the very top, unless you have a Dapper install CD that is)

Quit Nano by typing Control-X, and save the changes back to the same file. Now type:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

Installation will commence. You can even perform those steps now to upgrade to Dapper Flight 7, if you don't mind living adjacent to the edge.

EDIT: I was beaten by 3 minutes :-)[/QUOTE]


What do you mean by "...if you don't mind living adjacent to the edge."?

---

### Post by aysiu on 2006-05-13
I think it's a good idea to install the *desktop* package of whatever desktop environment you're using before you do the upgrade.

For example, if you're using Gnome, you would want to do ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` before changing up your sources.list and dist-upgrading to Dapper.

---

### Post by Hoffmann on 2006-05-13
[QUOTE=aysiu]I think it's a good idea to install the *desktop* package of whatever desktop environment you're using before you do the upgrade.

For example, if you're using Gnome, you would want to do ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` before changing up your sources.list and dist-upgrading to Dapper.[/QUOTE]

In your opinion, which of the alternative is the best for the upgrade:

(1) gksudo "update-manager -d"  or (2) changing up your sources.list and dist-upgrading?

Which one is the most safe?

---

### Post by aysiu on 2006-05-13
[QUOTE=Hoffmann]In your opinion, which of the alternative is the best for the upgrade:

(1) gksudo "update-manager -d"  or (2) changing up your sources.list and dist-upgrading?

Which one is the most safe?[/QUOTE] I know #2 works because I've used it. #1 is supposed to work.

**Edit**: After reading [this thread](http://www.ubuntuforums.org/showthread.php?t=175537), I wouldn't recommend #1.

---

### Post by dotdot on 2006-05-13
hey people i've just updated using 

gksudo "update-manager -d"



it failed a couple of times due to issues with the source.list file
commented out a couple of lines (which it was complaining about)
..then  it ran through no problem - and yes it did take a 
while... but hey i'm not in a big rush.

I now plan on updating all my boxes using the same process.

oh and btw the colours in dapper are STRIKING relative to what i saw in 5.10
ie a lot sharper and clear.

..cheers

..

---

### Post by drayan69 on 2006-07-07
I have received Dapper CD. Thanks to Canonical and Shipit..

I tried upgrading existing Breezy installation using CD. The problem with Synaptic is that despite adding CD to Repository, whenever I reload, it gives message CDROM can not be mounted. I am using Combo Drive having CD read/write and DVD read. The same is automounted as cdrecorder under /media folder.

I tried even after changing symbolic link cdrom linked to cdrecorder changing earlier link of cdrom0. Even this did not work.

I have already changed all instances of Breezy to Dapper in sources.list file.

Please help me. Thanks in advance.

---

