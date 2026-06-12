---
title: "aptitude displays two copies of each package, thinks everything is broken"
date: 2011-11-23
forum: General Help
---

### Post by Zxaos on 2011-11-23
I'm looking for some help to resolve an issue I'm having with aptitude (and maybe my sources.list?).

At some point after installing oneiric (it was a clean install), I've managed to screw up either my sources.list or aptitude's database. There are two main symptoms:
[LIST]
[*]Many packages displayed in aptitude show up twice
[*]Aptitude thinks my dependencies are broken, but everything works as far as I can tell.
[/LIST]

It looks like aptitude wants to remove many packages that depend on libraries like libc6 and libc-bin, even though they are installed.

Occasionally, when marking and unmarking packages in the UI, I get an error like
```
Internal error: the solver Install(nspluginviewer 1.4.4-0ubuntu3 <nspluginwrapper 1.4.4-0ubuntu3 -> {nspluginviewer 1.4.4-0ubuntu3}>) of a supposedly unresolved dependency is already installed in step 11
```

Can anyone suggest how I might start to troubleshoot this? Things aren't *broken* as far as I can tell, but I'm worried that at some point I'll install something or update something and the package manager will throw a fit and break my system.

My sources.list is below, in case I've done something stupid and have conflicting lines or something. I'd be happy to attach the proposed solution that aptitude wants to run, but I can't figure out how to extract it from the aptitude ui. I don't want to just run the solution, since I'm pretty sure it will break a lot of things that are installed since it'd be removing ~122 packages.

Any advice would be appreciated.

```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric main restricted
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates main restricted
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric universe
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric universe
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates universe
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric multiverse
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric multiverse
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates multiverse
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security main restricted
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security main restricted
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security universe
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security universe
deb http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security multiverse
deb-src http://ubuntu.mirror.rafal.ca/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

---

### Post by UnwashedMeme on 2011-11-23
I'm having the same problem. No ideas yet.

---

### Post by oldtimer7777 on 2011-11-23
> **UnwashedMeme said:**
> I'm having the same problem. No ideas yet.

Why is it configured to use *.ca???  Why not just use the MAIN repositories on a fresh install, at least until you can get everything the way you like it???

How did you configure your repos????

---

### Post by BC59 on 2011-11-23
But everything is duplicated on sources.list.

You have to uncheck all duplicate PPAs.

Go to Software Sources and to the tab Other Software and uncheck all, out of Canonical Partners and Independent (the default repositories). Then try to check again each one PPA , closing afterwards the Software Sources, to investigate where is the problem.

---

### Post by BC59 on 2011-11-23
Now I noticed that even the default repositories are duplicated.

Then write a 

```
sudo gedit /etc/apt/sources.list
```

and comment with hush (#) the duplicate PPAs

Like from 

> deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric multiverse
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric-updates multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric-updates multiverse


to look like

> # deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric multiverse
# deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric multiverse
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric-updates multiverse
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) oneiric-updates multiverse


Then save-exit and reboot

---

### Post by oldtimer7777 on 2011-11-23
I still can't understand how you hosed your source.list like this..   What was the last thing you did with your repos before this happened? Think about it for a minute.

> **BC59 said:**
> Now I noticed that even the default repositories are duplicated.

Then write a 

```
sudo gedit /etc/apt/sources.list
```and comment with hush (#) the duplicate PPAs

Like from 



to look like



Then save-exit and reboot

---

### Post by Zxaos on 2011-11-23
> **oldtimer7777 said:**
> Why is it configured to use *.ca???  Why not just use the MAIN repositories on a fresh install, at least until you can get everything the way you like it???

How did you configure your repos????

They're .ca ones because the canadian mirrors are significantly faster for me, and have never caused problems in the past :)

As for what I last did before they were so hosed... I honestly don't know. It's been broken for a while now and I haven't had the time to fix it. I don't recall doing anything particularly weird to the sources list - in fact I think they only time I edited it by hand was to uncomment the partner repositories.

I'll remove all the duplicates when I get back to that machine tomorrow (I didn't even notice them before, although now I wonder how I could have missed it #-o), but I'm unconvinced it will solve the phantom dependency issue. I guess we'll see.

Thanks for the lead though!

---

### Post by Zxaos on 2011-11-24
Well...

That fixed the problem of packages that aren't installed being displayed twice. However, aptitude still thinks there's a huge dependency issue going on.

For example, it wants to remove libc6. It lists libc6 as installed twice, but says one of them has to be removed because it depends on libgcc1. libgcc1 is listed (twice) and aptitude wants to remove one of them because it's depends on libc6.

I'd go ahead with this, since it seems to be removing duplicate packages, except there are many packages which are only installed once and will be removed because of dependency errors (for example flashplugin-downloader).

Maybe I'll just take a tar backup of my entire system and let aptitude do what it's going to do... see what breaks.

---

### Post by angryfirelord on 2011-11-24
I believe this is an issue with multiarch support, which aptitude apparently chokes up on. Go to a terminal and type this:
```
sudo nano /etc/dpkg/dpkg.cfg.d/multiarch
```
Put a # next to the first line. It should look this. (All this does is comment it out)
```
#foreign-architecture i386
```
Run aptitude update again and see if this fixes the problem.

If you do need multiarch, you'll have to stick with apt-get.

---

### Post by Zxaos on 2011-11-25
Hey! It *is* multiarch support that was the culprit - I actually noticed this when I told aptitude to fix everything yesterday, and it removed a bunch of i386 libraries.

---

### Post by rcsheets on 2011-12-03
If you are experiencing this bug, you might want to follow and/or vote for it on Launchpad: [https://bugs.launchpad.net/ubuntu/precise/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/precise/+source/aptitude/+bug/831768)

---

### Post by psihokiller4 on 2011-12-03
> **BC59 said:**
> Now I noticed that even the default repositories are duplicated.

Then write a 

```
sudo gedit /etc/apt/sources.list
```and comment with hush (#) the duplicate PPAs

Like from 



to look like



Then save-exit and reboot


ammmm what?!?
why do you need to reboot that doesn't reload repos as far as I know you only need to reload repos

---

### Post by rcsheets on 2011-12-15
> **psihokiller4 said:**
> ammmm what?!?
why do you need to reboot that doesn't reload repos as far as I know you only need to reload repos

You are correct. There should be no need to reboot.

---

