---
title: "Synaptic Package Manager Problems"
date: 2006-03-19
forum: General Help
---

### Post by CJs06 on 2006-03-19
Howdy, I hope someone can answer my question because googling the problem didn't return any answers.

My problem is that after I opened the add applications, and clicked on the mplayer under sound/video, which asked me to add a repository. It then procceded to install the repository and restart the manager. After that every time it starts it crashes without any errors or messages.

My guess is to reinstall the manager somehow but I'm not for sure.

Any help would be appriciated, thx.

---

### Post by dermotti on 2006-03-19
Hmm maybe take a look at your /etc/apt/sources.list and see if there something funky in there.

---

### Post by CJs06 on 2006-03-19
There isn't anything wierd that I know of.

Heres whats in side.
___________________________________________________________________________
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse
__________________________________________________________________________

Other than that I don't know.

I tried installing synaptic manually, by downloading it off thier site and it had errors installing; dependency errors on alot of things, which I know I have.

---

### Post by RAOF on 2006-03-19
Could you run synaptic from a terminal - that way you'll be able to see any messages it spits out before dying.  Run
```
gksudo synaptic
```
And post whatever errors that produces.

---

### Post by CJs06 on 2006-03-19
Ok, got an error.

____________________________________________________________________________
synaptic: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: No such file or directory.
____________________________________________________________________________

But what is wierd, is i followed a how-to guide on getting extra repositories by adding to the /etc/apt/sources.list seeing that It might make it try and get more repositories to get it running, which it did. This fixed the Add Applications program but when I try to use Synaptic it still fails to run.

---

### Post by CJs06 on 2006-03-20
Bump

---

### Post by RAOF on 2006-03-20
Sounds like you're missing one of the dependencies to synaptic.  I'd try running **sudo apt-get remove synaptic** followed by **sudo apt-get install synaptic** from a terminal.  That should re-install any dependencies you're missing.

Failing that, you may have inadvertantly added wierd, crazy debian repositories to your sources.list, and installed a different/differently named version of the dependency.  If the above doesn't work, we can investigate this.

---

