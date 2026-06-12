---
title: "Package Manager error"
date: 2010-02-13
forum: General Help
---

### Post by The3irikr on 2010-02-13
Ok, so i just upgraded to ubuntu 9.10 and when i open software center nothing pops up. Now I have this red circle with a white line through it on the top of the screen. When I put my cursor over it, it say...

An error occurred, please run Package Manager from the right-
click menu or apt-get in a terminal to see what is wrong.
The error message was: ' Error: Opening the cache (E: Type
'30016' is not known on line 1 in source list /etc/apt/
sources.list.d/karmic-partner.list, E:The list of sources could 
not be read.)'This usually means that your installed packages
have unmet dependencies


ok so i'm a huge noob at Ubuntu. I know the basics but this is over my head.

---

### Post by rcayea on 2010-02-13
Maybe you could uncheck the referenced sources in the software sources under the Administration tab.

---

### Post by The3irikr on 2010-02-13
well i've looked there and for some reason i thought they were supposed to be checked so i checked them all but when I refresh them i get this message...

E: Type '30016' is not known on line 1 in source list /etc/apt/sources.list.d/karmic-partner.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by drs305 on 2010-02-13
Since you said you are a newbie, I'll expand on what the previous poster wrote, which would solve your problem. 

When you try to update, Ubuntu looks at the repository lists to see where to go to find the files. One of your lists isn't in the correct format, so Ubuntu is complaining.

To do what the previous poster wrote, you can amend your sources by either opening Synaptic or Software Sources. Go the main menu and select Software Sources or Synaptic, Settings, Repositories, Other Software/Third Party software. Untick/deselect the one that ends with "karmic partner". Then hit the "Reload" button on the Synaptic/Software Sources menu.

You should be able to run the updates. After hitting "Reload", you should also be able to reselect the "partner" tick box, which will reactivate the list with the proper formatting.

---

### Post by The3irikr on 2010-02-13
i don't have anything that ends with a karmic....
just jaunty partner and jaunty partner source code....

---

### Post by drs305 on 2010-02-13
> **The3irikr said:**
> i don't have anything that ends with a karmic....
just jaunty partner and jaunty partner source code....

According to the error message, the problem is with a karmic file. Are you running jaunty? If so, open a terminal and run this command and tell us if the error is fixed:
```
sudo mv /etc/apt/sources.list.d/karmic-partner.list /etc/apt/sources.list.d/karmic-partner.list.bad
```

If you haven't used "sudo" in a terminal before, you will be asked for your password. As you type it, you won't see it being entered. Just continue to type and press ENTER when you are done.   The command renames the corrupt file so Ubuntu won't find the error when it runs the update.

Otherwise post the results of this command:
> cat /etc/apt/sources.list.d/karmic-partner.list

---

### Post by The3irikr on 2010-02-13
wow... thanks a BUNCH!!!!!
It works but the red circle is still up there....
well, if it acts up again i'll just say so...

---

### Post by paul_in_london on 2010-02-13
Jaunty is 9.04, but you said you've upgraded to karmic (9.10)?

```
sudo gedit /etc/apt/sources.list
```

If you want to use karmic, replace occurrences of jaunty[COLOR="Red"] [/COLOR] with karmic[COLOR="Red"][/COLOR] and save the file. Then do:

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by The3irikr on 2010-02-13
Ok, I got a big list so when you say "replace occurrences of jaunty with karmic"
you mean i just erase all jaunty words and replace them with karmic??

srry, i'm just being cautious.

---

### Post by paul_in_london on 2010-02-13
Yes, just do a global replace of jaunty with karmic, save the file and then run the update and upgrade commands I posted.

Actually, before you do that can you post the output of:

```
sudo dpkg --configure -a
```

When you're editing the file, use the Replace All option from the Search menu.

Sorry I typed --a by mistake, it should have just been -a

---

### Post by The3irikr on 2010-02-13
dpkg: unknown option --a

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

i g2g now... so i'll replay later

---

### Post by paul_in_london on 2010-02-13
You want to make your /etc/apt/sources.list file look like this:

```
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic main restricted
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates main restricted
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic universe
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic universe
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates universe
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic multiverse
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic multiverse
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates multiverse
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security main restricted
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security main restricted
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security universe
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security universe
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security multiverse
deb [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://ubuntu-archive.datahop.it/ubuntu/](http://ubuntu-archive.datahop.it/ubuntu/) karmic-security multiverse
```

except that you don't need to change your mirror.

---

### Post by paul_in_london on 2010-02-13
I edited my earlier post. The command should have been:

```
sudo dpkg --configure -a
```

---

### Post by jltrain on 2010-02-14
Hi I have the same problem. I get "Warning Can't read module/lib/modules/2.6.31.20"

---

