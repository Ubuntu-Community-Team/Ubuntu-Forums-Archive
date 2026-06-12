---
title: "The Big move to Dapper Final"
date: 2006-05-30
forum: General Help
---

### Post by seanUSXIII on 2006-05-30
How many of you will be using apt-get dist-upgrade to move from dapper beta to dapper final? I'm probably using the disc and re-installing, just becuase I'm on dial-up. I should have my serial modem by then (finally a working modem :D  ). What is the suggested way to go from beta to final?

---

### Post by tsb on 2006-05-30
An upgrade is 99.9% the same as a reinstall and I already did a reinstall with RC so it's reasonable "fresh" anyway.

---

### Post by seanUSXIII on 2006-05-30
[QUOTE=tsb]An upgrade is 99.9% the same as a reinstall and I already did a reinstall with RC so it's reasonable "fresh" anyway.[/QUOTE]

If I just do the upgrade, do I get to keep cool things like my Compiz/XGL installation?

---

### Post by henriquemaia on 2006-05-30
Don't get me wrong, but aren't all these polls that are coming about on this forum more suited to the Ubuntu Cafe?

Just a thought, though.

---

### Post by Bavo on 2006-05-30
I'm on dapper for a while now, i used dist-upgrade and it worked perfectly

but when dapper final is there i will do a clean install.
There are a few reasons why i'll do that, but it wouldn'd be really nessesary

The most important reasons are:
- A nice clean computer (i try loads of software which i remove or not, but they often leave dependencies, so reinstalling from scratch will clean up my computer)
- I like to know what a clean install looks like, what i will have to configure etc .., in case i have to install it on an other computer.

But if you don't want to reinstall your computer, there is no reason to do so, dist-upgrade will work just fine

---

### Post by seanUSXIII on 2006-05-30
[QUOTE=henriquemaia]Don't get me wrong, but aren't all these polls that are coming about on this forum more suited to the Ubuntu Cafe?

Just a thought, though.[/QUOTE]

Well, this is a valid question about the dapper beta and how to upgrade. I'm still a newb and haven't been into ubuntu long enough to have ever done a dist-upgrade before. I have noticed a bazillion polls about dapper lately though. Oh well what do you expect when its almost time for such a great distro's release. :D

---

### Post by effoff on 2006-05-30
Back up your pr0n to a CD, and do a dist-up..., if it doesn't work, go for the CD.

---

### Post by ubuntu_demon on 2006-05-30
just use the update-manager to easily upgrade to Dapper

---

### Post by seanUSXIII on 2006-05-30
[QUOTE=effoff]Back up your pr0n to a CD, and do a dist-up..., if it doesn't work, go for the CD.[/QUOTE]

LMAO!!! I more or less don't want to go through installing XGL again if I don't have to. Doing a dist-upgrade would probably take forever over dial-up wouldn't it? Is there a way to dist-upgrade from a file, say, that maybe I could download over my T1 line at work :D

---

### Post by aysiu on 2006-05-30
You can upgrade from the alternate install CD, not the desktop CD.

Just add is as source in Synaptic (Edit > Add CD-ROM) and comment out all your other repositories (uncheck their boxes in Settings > Repositories).

---

### Post by nickle on 2006-05-30
If you are moving from Breezy, seriously consider a fresh install; an attempted update killed my system and i had to do a fresh install anyway.
Beginners, regardless what you do BACK UP all your important stuff...

---

### Post by doobit on 2006-05-30
Since I have been using the Dapper Xubuntu since Beta, I already have customized it a lot and would hate to start over. The upgrade has been working fine so far...

---

### Post by Lord Illidan on 2006-05-30
[quote=nickle]If you are moving from Breezy, seriously consider a fresh install; an attempted update killed my system and i had to do a fresh install anyway.
Beginners, regardless what you do BACK UP all your important stuff...[/quote]

I second this.

Also, make sure that you have a seperate /home partition. It is very convenient, just format the / partition, and the rest of your data will remain intact.

For my part, I've been using Dapper since Flight 2, I believe... without any major hitches. All I need is to do apt-get dist-upgrade

---

### Post by aysiu on 2006-05-30
[QUOTE=Lord Illidan]
Also, make sure that you have a seperate /home partition. It is very convenient, just format the / partition, and the rest of your data will remain intact.[/QUOTE] If you don't have one, create one:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Rikostan on 2006-05-30
I need a fresh install on one of the laptops, but that was because it was the the first that machine saw Ubuntu. I did a dist-upgrade on my machine last week and it went pretty smoothly.

---

### Post by seanUSXIII on 2006-05-30
[QUOTE=aysiu]If you don't have one, create one:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)[/QUOTE]

I actually have two seperate physical disks. One of my 250GB's is for OS'es (3 of em right now) and the other is for music, pics, multimedia and what-not. Is there a big advantage to making a "home" partition?

---

### Post by hobbit1983 on 2006-05-30
I dist-upgrade using the nice pretty GUI tool.  Before I did this I backed up /home, however I didn't need to worry the entire update went really smoothly.  

I did consider a fresh install but have so much installed the idea of hosing my disk didn't seem like a fun idea

---

### Post by christhemonkey on 2006-05-30
I think im going to need to do a fresh install, due to completely and utterly borking my current install.

(which has only been upgraded since hoary)

---

### Post by aysiu on 2006-05-30
[QUOTE=seanUSXIII]I actually have two seperate physical disks. One of my 250GB's is for OS'es (3 of em right now) and the other is for music, pics, multimedia and what-not. Is there a big advantage to making a "home" partition?[/QUOTE] The only advantage would be your settings remaining intact (how you customized your desktop) and your emails and web browser preferences and bookmarks not being lost.

I generally back up my Firefox and Thunderbird settings onto a separate data partition instead of having a separate /home partition.

---

### Post by LMP900 on 2006-05-30
I voted for a complete reinstall, only because I have a couple of systems I want to put Dapper on, and the fact that I'll have a live cd handy wheneve I need it.

---

### Post by Pausanias on 2006-05-30
I don't understand. If you have dapper beta installed, don't you automatically get all the new packages for Dapper Final by just running the update manager as you would normally? Is there a need for "dist-upgrade"?

[QUOTE=seanUSXIII]How many of you will be using apt-get dist-upgrade to move from dapper beta to dapper final? I'm probably using the disc and re-installing, just becuase I'm on dial-up. I should have my serial modem by then (finally a working modem :D  ). What is the suggested way to go from beta to final?[/QUOTE]

---

### Post by aysiu on 2006-05-30
Pausanias is right.

If you already have Beta installed, just paste this command into the terminal on June 1: ```
sudo aptitude update && sudo aptitude dist-upgrade
``` Otherwise, you should get a notification of updates, and I can't imagine there will be that many between now and Thursday.

---

### Post by Pausanias on 2006-05-30
Now I'm really confused. Why do you need to do dist-upgrade if you have the Beta installed?

Or did you mean to say "If you *don't* already have Beta..."

[QUOTE=aysiu]Pausanias is right.

If you already have Beta installed, just paste this command into the terminal on June 1: ```
sudo aptitude update && sudo aptitude dist-upgrade
``` Otherwise, you should get a notification of updates, and I can't imagine there will be that many between now and Thursday.[/QUOTE]

---

### Post by xinix on 2006-05-30
New install for me as well.  I dist-upgraded from breezy sometime around flight 5.  I'd like to start out with a fresh setup.  The other reason is that I've really treated this as a sandbox to play with things that I really have no interest in keeping and I'm too lazy to track down and uninstall each package.

---

### Post by Scunizi on 2006-05-30
I will be doing a clean install only for the hope that I can get my laser printer working ... So far everything I've tried doesn't work even though I have a PPD driver for it, installed, visable, seemingly functional but broke.

---

### Post by aysiu on 2006-05-30
[QUOTE=Pausanias]Now I'm really confused. Why do you need to do dist-upgrade if you have the Beta installed?

Or did you mean to say "If you *don't* already have Beta..."[/QUOTE] *upgrade* upgrades only existing packages. *dist-upgrade* will add and remove appropriate packages to get the full changes for the newest version of Dapper.

For example, if Beta had packages A, B, and C and Dapper had packages A, C, and D...

*upgrade* would just get the newest versions of packages A, B, and C.
*dist-upgrade* would upgrade packages A, and C, remove package B, and add package D.

---

### Post by Mathias-K on 2006-05-30
Normally I would have used aptitude, but my current main desktop install is an old Kubuntu Breezy install overwritten with a rather trashed Kubuntu Dapper Alpha and then the new Ubuntu Dapper Beta on top. Add a somewhat clumsy install (used a couple of methods on my way ;)) of Xgl and you've got a system as trashy as my XP laptop :mrgreen:

I think I'll just grab a final CD and clean up the mess..

---

### Post by escape on 2006-06-01
Wow. I can't believe so many people are reinstalling. If you were upgrading from Breezy to Dapper, I would certainly say reinstall, but the differences between Dapper Beta and final are much less significant. Especially if you've been upgrading consistently while using beta, it is almost ridiculous to reinstall: you basically already have Dapper Final.

---

### Post by Zdravko on 2006-06-01
[escape]("http://www.ubuntuforums.org/member.php?u=63145"), some people are still using Breezy. That is why I am waiting for the official stable release to download.

---

### Post by blakamin on 2006-06-01
I just ran apt-get dist-upgrade and got nothin!

All sorted from when I ran update in synaptic 45 minutes ago maybe??? 

how can I tell?

---

### Post by kvonb on 2006-06-01
A fresh install is good practice.

I am fast at doing a Win install because of all the practice I've had, plus I will be doing a lot of Dapper installs (standard on new machines I sell retail).

There is something nice about a fresh install, a bit like cleaning your car after a whole year of neglect!

Ayway, it's just plain FUN :D

---

### Post by AlphaMack on 2006-06-01
I reinstalled when the RC came out.  Then I updated daily until about 2 days ago when the river was finally dammed.  It sure made a difference from dist-upgrading from Breezy since I saved about 10% of my HDD from crud.

---

### Post by LORD_PoLvO on 2006-06-01
heh ill just get the disk because i also have to install on pcs without an internet conection lol

---

### Post by bvanaerde on 2006-06-01
I'm going to do a fresh install, because I'm going to remove Windows XP completely from my laptop. Until now, I had a dualboot...

---

### Post by Deanodriver on 2006-06-01
I'm going to reinstall, because I upgraded from Breezy-Dapper Beta-Dapper Final, and I kinda want to fix a few things I mangled with the Breezy-Beta upgrade :)

---

### Post by beercz on 2006-06-01
I have only installed Ubuntu from disk once - the first time I installed it - it was Warty!
I have upgraded every time and have been using Dapper since November 2005.

---

### Post by bluenova on 2006-06-01
I would pick the missing option:

3. Wait for the update manager to inform that a new version is available.

---

