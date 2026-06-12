---
title: "Does Emerald not work on Xubuntu 11.04?"
date: 2011-04-29
forum: General Help
---

### Post by neu5eeCh on 2011-04-29
OK, trying a different title... If I can't get satisfaction, then I'll give it a rest.

1.) Installed Xubuntu 11.04
2.) Installed Compiz, Fusion, CCSM, & Emerald.
3.) Compiz works.
4.) Emerald doesn't.
5.) Using Fusion to set the WM or typing [emerald --replace] (in CCSM) doesn't work. Xubuntu seems unwilling to cooperate with **any** WM if it's not XFWM.

Has anyone here gotten Emerald to work in Xubuntu 11.04?

---

### Post by lykwydchykyn on 2011-04-29
I haven't.  I switched to XFCE briefly from KDE because of some driver issues on my work system; tried to snazz it up with compiz and it was just unmanageable.  Emerald segfaulted whenever I ran it, and for some reason compiz used the KDE window decorations and behaved bizarrely no matter what I did.  I thought it was just my setup, since I had KDE installed and who-knows-what cruft left in my home directory from bygone setups (used to run compiz + KDE3 back in the day).

Eventually I gave up and decided to try to fix KDE instead.

---

### Post by nowell29 on 2011-04-30
Same problem. Been that way since the Beta 2, but I have no solution.  :(  
I miss my wobbly windows :)
loving everything else though!

---

### Post by rawdmon on 2011-04-30
This is one of those "Just wow" moments with Ubuntu.  Does no one test this stuff beforehand?  I saw some patch guide for getting Emerald working that involved building it from source, but the git link that they gave doesn't even pull down a configure file so it's useless.  I really hope that they sort this thing out since my window theme is useless until they do.

---

### Post by neu5eeCh on 2011-04-30
Thanks for all your responses. I **do **appreciate it, most of all because it will save me from looking for solutions that don't exist.

---

### Post by Darent on 2011-04-30
Doesn't work for me neither... i'm stuck with compiz+shitty metacity decorator... And the building solution doesn't work.

---

### Post by neu5eeCh on 2011-04-30
If any of you meet with an XFCE distro in which Emerald works (and you like it) please pass it on.

I tried Mint XFCE (before Xubuntu) but didn't like that Mint was still using 4.6 (instead of 4.8 ); and was unhappy about the overall font display (very poor).

---

### Post by mc4man on 2011-04-30
> **rawdmon said:**
> This is one of those "Just wow" moments with Ubuntu.  Does no one test this stuff beforehand?  I saw some patch guide for getting Emerald working that involved building it from source, but the git link that they gave doesn't even pull down a configure file so it's useless.  I really hope that they sort this thing out since my window theme is useless until they do.
A git source like that needs a ./autogen.sh to be run first to create a configure script
As far as ubuntu - it's not their problem emerald doesn't work correctly or at all in 11.04

---

### Post by tomski on 2011-05-01
i been using a fresh install of xubuntu 11.04

it seems that emerald for some reason has fallen by the way side & has not been developed on for some time,
whether this is due to canonical pushing with unity & it's dumb *** settings dumped into the compiz settings screen (total lazyness imho) i'm not sure but there are only a handfull of GTK themes i like & would love to get my glass borders back.

In the meantime i have found that if you completely remove emerald this forces compiz to either create it's own or gtk 
at least you get wobbly windows tho lol
also if you have some real odd behavior from compiz try clicking on preferences within compiz settings then reset your profile to defaults, then when you login it should work

goodluck in getting a logical working & productive desktop now that ubuntu is all unafy

just hope i can get wine drinkable again!

---

### Post by Darent on 2011-05-02
If somebody is interested, there's a compiled version of emerald than works in:

[https://bugs.launchpad.net/bugs/726229](https://bugs.launchpad.net/bugs/726229)

Look in the comment #20 Vanessa atached a working version of emerald in deb format (32 bit only)

It worked for me.

Good luck!

EDIT: Forgot to say i'm not in xubuntu, i use gnome desktop. But anyway since emerald is a separated process i think the problem and the patched emerald would work the same.

---

### Post by andrewthomas on 2011-05-02
> **rawdmon said:**
> This is one of those "Just wow" moments with Ubuntu.  Does no one test this stuff beforehand?  I saw some patch guide for getting Emerald working that involved building it from source, but the git link that they gave doesn't even pull down a configure file so it's useless.  I really hope that they sort this thing out since my window theme is useless until they do.

I just got this to work.

First make sure that you don't have any emerald or libemeraldengine-dev package installed then:
```

mkdir emerald++
cd emerald++
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald/
git checkout -b compiz++ origin/compiz++
./autogen.sh --prefix /usr
make
sudo checkinstall 
# version 0.9.4
```if it fails then
```
sudo dpkg -i --force-all emerald_0.9.4-1_amd64.deb
```download [http://cgit.compiz.org/fusion/decorators/emerald-themes/snapshot/emerald-themes-0.6.0.tar.bz2](http://cgit.compiz.org/fusion/decorators/emerald-themes/snapshot/emerald-themes-0.6.0.tar.bz2)
extract
```
cd emerald-themes-0.6.0
./autogen.sh --prefix /usr
make
sudo checkinstall
```Works like a charm.

Here are two amd64 packages that I built on oneiric


[http://dl.dropbox.com/u/27872107/emerald-themes_0.6.0-1_amd64.deb](http://dl.dropbox.com/u/27872107/emerald-themes_0.6.0-1_amd64.deb) [http://dl.dropbox.com/u/27872107/emerald_0.9.4-1_amd64.deb](http://dl.dropbox.com/u/27872107/emerald_0.9.4-1_amd64.deb)

---

### Post by dmillerct on 2011-05-02
Wow! Thank you Vanessa Ezekowitz!!!

The deb file posted in comment 20 worked for me and I now have my nice minimal glass boarders back.

---

### Post by chargersfan420 on 2011-05-10
Thank you andrewthomas!  Your 64-bit deb files worked great!  This will definitely help me attempt the switch from gnome 2.x to XFCE.  Also, holy crap, everything runs faster in XFCE.

---

### Post by neu5eeCh on 2011-05-10
The *AMD64.deb works on a 32 bit system?

---

### Post by Darent on 2011-05-11
> **VTPoet said:**
> The *AMD64.deb works on a 32 bit system?

I don't think the 64 works in 32 bit (it uses to be the other way round) but  if you look in my comment in the previous page of this tread there's a  link to a launchpad bug repport with the 32 bit deb

[https://bugs.launchpad.net/bugs/726229](https://bugs.launchpad.net/bugs/726229)

Look for comment number #20 in that web, the deb is the atached "working version of emerald"

good luck!

P.D. Funny, but in the time i've been without emerald i found a nice gtk theme and now emerald works but I'm not using anymore... xD

---

