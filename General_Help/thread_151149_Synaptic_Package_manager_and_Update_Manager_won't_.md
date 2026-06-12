---
title: "Synaptic Package manager and Update Manager won't start"
date: 2006-03-27
forum: General Help
---

### Post by Titi on 2006-03-27
hello,

i just nstalled ubuntu breezy badger (again). and when i click Synaptic package manager or update manager, nothing happens. it's the same with some other applications...
during install, there were some complications, something when choosing a mirror, i tried several, but none of them seemed to work, so i skipped that part, and then there was some problem with 'apt', i don't know what it was. 
for the rest, ubuntu works just fine...

thanks in advance

M.

---

### Post by aysiu on 2006-03-27
Can you type these two commands in the terminal and post the output here? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by invalid on 2006-03-27
Try running the program from a terminal and seeing what output you get. Paste the output here, and maybe we can debug it for you.

Open a terminal and type:
```
sudo synaptic
```

---

### Post by cormic on 2006-03-27
I just installed ubuntu and update is not working correctly.  Here is the output as requested above.

[SIZE="1"]Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release.gpg [189B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Fetched 1B in 4s (0B/s)
Reading package lists... Done


deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
# The above lines were generated automatically by EasyUbuntu.
# The rest of your sources.list follows




## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
[/SIZE]

---

### Post by Titi on 2006-03-27
[QUOTE=aysiu]Can you type these two commands in the terminal and post the output here? ```
sudo apt-get update
cat /etc/apt/sources.list
```[/QUOTE]

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r estricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted unive rse multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted u niverse multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Titi on 2006-03-27
[QUOTE=invalid]Try running the program from a terminal and seeing what output you get. Paste the output here, and maybe we can debug it for you.

Open a terminal and type:
```
sudo synaptic
```[/QUOTE]

this gives no output at all...

---

### Post by aysiu on 2006-03-27
**cormic,**

Everything appears to be working fine on the back end of things. You have an EasyUbuntu sources.list (I've never seen one of those before), but it appears to be working... on the back end, as I said before.

Now, the front-end is Synaptic Package Manager. What's the problem exactly? Can you start Synaptic Package Manager? What happens when you click "Reload"?

**Titi**,

The only source in your repositories list is the Ubuntu CD. Do you see all those # signs? A # sign at the beginning of a line basically says to Ubuntu, "Ignore this line."

Now, that doesn't explain why Synaptic Package Manager won't start, but it's just something to note.

When you say there's *no* output to *sudo synaptic*, what do you mean, exactly? Does *anything* happen? Does it go to the next line? Does it not go to the next line?

Have you tried this? ```
gksudo synaptic
```

---

### Post by cormic on 2006-03-27
hi aysiu,

Thanks for the feedback - I installed easyubuntu and it may have commented out the other entries from the sources.list - I uncommented them and everything is back working.  :D

---

### Post by Titi on 2006-03-27
[QUOTE=aysiu]

When you say there's *no* output to *sudo synaptic*, what do you mean, exactly? Does *anything* happen? Does it go to the next line? Does it not go to the next line?

Have you tried this? ```
gksudo synaptic
```[/QUOTE]

it does go on to the next line, but nothing else happens. same thing with gsudo synaptic.

(thanks for the quick replies btw)

---

### Post by aysiu on 2006-03-27
[QUOTE=Titi]it does go on to the next line, but nothing else happens. same thing with gsudo synaptic.

(thanks for the quick replies btw)[/QUOTE] That's not good. That's really not good.

Does that happen for any command you type, or only ones with *sudo* in front?

For example, if you type ```
ls
df -h
free
``` do you get actual output, or does it just go to the next line?

And if you type ```
sudo fdisk -l
sudo apt-get update
``` do you get actual output, or does it just go to the next line?

---

### Post by Titi on 2006-03-28
[QUOTE=aysiu]That's not good. That's really not good.

Does that happen for any command you type, or only ones with *sudo* in front?

For example, if you type ```
ls
df -h
free
``` do you get actual output, or does it just go to the next line?

And if you type ```
sudo fdisk -l
sudo apt-get update
``` do you get actual output, or does it just go to the next line?[/QUOTE]

ok, i did all those things and i got:

> maarten@Maarten:~$ ls
Desktop
maarten@Maarten:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             3,9G  1,6G  2,1G  44% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-9-386/volatile
/dev/hda1              28G   19G  9,7G  66% /media/hda1
/dev/hda5              45G  6,2G   39G  14% /media/hda5
/dev/hdb5             190G   88G  103G  46% /media/hdb5
maarten@Maarten:~$ free
             total       used       free     shared    buffers     cached
Mem:        516492     330748     185744          0      12584     192652
-/+ buffers/cache:     125512     390980
Swap:            0          0          0
maarten@Maarten:~$ sudo fdisk -l
Password:
maarten@Maarten:~$ sudo apt-get update
maarten@Maarten:~$

---

### Post by That Other Guy on 2006-03-28
These symptoms are EXACTLY what I've got happening at work.  Installed 5.10 today, and needless to say, not having sudo working put a serious bind on getting the computer back up & running (and getting my work done).

FWIW, I downloaded the installer CD just last night.

Mike

---

### Post by aysiu on 2006-03-28
[QUOTE=Titi]ok, i did all those things and i got:[/QUOTE] Okay...

1. That's just what I'd guessed.
2. That's bad.

It means there's something wrong with the sudo permissions. Unfortunately, I don't know how to fix this. I did this to my own system accidentally once when I was playing around with the command line, deleting and creating new users and passwords (I didn't know what I was doing).

The only fix I could think of was reinstalling.

There probably is a relative easy fix for this, but I don't know it.

---

### Post by That Other Guy on 2006-03-28
Here's my guess: I just did an install on a 2nd machine, also in expert mode, (at home), and noticed that one of the installer screens asked for, what could be interpreted to be, additional 'sections' (or steps) to load during the installation.  That's pretty vague, but I'm not sure how else to describe them, and I don't recall how the screen was worded.

The screen said that all NECESSARY 'sections' should already be selected, but you could select additional ones if you felt they were needed.  This could be read that nothing else needs to be selected for most installations, when in fact one or more are mandatory for a functioning system.  This is just my newbie guess.  I've been running Linux for a few years now, but Ubuntu is new to me.

Another problem, both here and at the other machine, is that neither http nor ftp would connect to the unbuntu.com repository during installation.  The network connection is fine, however.

---

### Post by Titi on 2006-03-29
[QUOTE=That Other Guy]
Another problem, both here and at the other machine, is that neither http nor ftp would connect to the unbuntu.com repository during installation.  The network connection is fine, however.[/QUOTE]

indeed, exactly the same problem here.
what to do, what to do??

---

### Post by That Other Guy on 2006-03-29
I didn't have anything new commited to this install, so I just reinstalled it under the normal mode (i.e. not expert).  While I'm the first to admit these problems were most likely my fault, I have to say I'm not a fan of the 'expert' mode installer.  No, not because it's in ncurses - I've been running Slackware for 3 years and am quite comfortable with it.  My issues are that there's no way to go back effectively and re-do options.  For example, the screen asking about using hdparm with the CD drive: it asks something to the effect of, " do you want to use extra parameters?", implying a 'yes' or 'no' answer.  Nope - that causes a failure in the installation that you can't go back and change.  It should be phrased to something like, "enter additional hdparm parameters here, orleave blank for none."

The questions for additional packages that I referred to above could be worded much better, too. Instead of saying, "necessary packages should already be selected," though NONE were, and leaving the user to think that everything shown was optional, it should be fixed to ensure that necessary packages are already checked and possibly ghosted to prevent inadvertant removal.

But anyway... the standard installation mode works fine on two machines, and I'm starting to explore Unbuntu (actually Kubuntu...).

Sorry I didn't have a magic fix for you, Titi.

---

### Post by Dropknee on 2006-04-01
I do a clean install to my external HDD and when I try to use the updater , nothing happen...... dont know why this happen, few month ago I intall ubuntu in the same way and all work without any problem

---

