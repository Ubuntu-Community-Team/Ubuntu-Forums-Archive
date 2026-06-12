---
title: "Software Catalogue?"
date: 2011-11-15
forum: General Help
---

### Post by jony121 on 2011-11-15
using 11.10
Opened software centre. It said something about broken software catalogues, do I want to fix. I said yes. It said something about fixing deps and kindly un-installed a bunch of my software!!! Of course I can re-install but this was seriously annoying! EDIT: PS, it was 39 apps! That is a serious amount of install before work tomorrow!

Also, I wanted to install gens/gs and it came up with this message:
"If you install gens/gs future updates will not include new items in The Ubuntu Desktop system set. Are you sure you want to continue?"

DAFUQ! Seriously Software Centre... Seriously!

I got gens/gs installed, just not via the software centre.

Can anyone explain why these things happened and what would be best course of action in the future?

Edit2:
[IMG]http://img6.imagebanana.com/img/32kn1fkh/_032.png[/IMG]
can they seriously be conflicting?

---

### Post by An Sanct on 2011-11-15
LOL, Seriously! :)

I personally would install synaptic package manager (DAF__-why is it not installed by default???)

And then I would check for consistency of the SW, maybe that would give you a hint to what is bothering your system, as this is *not normal* behavior...

PS. from terminal "apt-get install -f" might provide the same result, I just like the GUI option better :) (sudo of course!)

---

### Post by hansdown on 2011-11-15
> **An Sanct said:**
> LOL, Seriously! :)

I personally would install synaptic package manager (DAF__-why is it not installed by default???)

And then I would check for consistency of the SW, maybe that would give you a hint to what is bothering your system, as this is *not normal* behavior...

PS. from terminal "apt-get install -f" might provide the same result, I just like the GUI option better :)

I was going to suggest that, but the packages, don't seem, to be in synaptic.

---

### Post by An Sanct on 2011-11-15
> **hansdown said:**
> I was going to suggest that, but the packages, don't seem, to be in synaptic.

A-ha ... I dug around for the package "gens", and it seems, that 11.10 somehow made it and some other i386 - into an orphan, due to the fact, that 11.10 is the first multiarch. As far as I could understand, that means, that Ubuntu does not need the x86/x64 differentiation any more (supposedly, I personally can neither confirm or deny this... I just trust them or I totally misunderstood the concept ...)

There are third party solutions, workarounds and hacks ... so again [WARNING] this are third party things, so use with caution and make sure you understand what you are doing :)

I've put the things I found in a "code" container ... so that links wont be broken...
```
http://www.ubuntuupdates.org/ppa/getdeb_games?dist=oneiric
http://www.gens.me/
http://www.ubuntuupdates.org/packages/show/369880
http://forums.sonicretro.org/index.php?showtopic=26538&st=0&p=623906&#entry623906
(the last one from here) http://forums.sonicretro.org/index.php?showuser=8520&tab=topics

All found with googling for "Ubuntu 11.10 package information gens"
```Two things: 
1. Be sure to understand what you are doing if you follow third party advice! (did I mention, this includes my advice too!)
2. WHY is there no synaptic in Oneiric or in Precise ??? It's 2.2MiB for crying out loud ... I know the border was moved up to 750Mb (cca. 1.07 CD!) so *why* not include a normally hidden Admin power-tool? No ... rather include two types of card games, sudoku and "mine sweeper" ...

---

### Post by hansdown on 2011-11-15
Nice work, An Sanct.  :D

---

### Post by jony121 on 2011-11-16
> **An Sanct said:**
> apt-get install -f

output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 lib32bz2-1.0 libsm-dev libcaca-dev ia32-libs-multiarch:i386
  libqt4-declarative:i386 liblcms1:i386 libqt4-qt3support:i386 libslang2-dev
  libcupsimage2:i386 ufoai-server-data lib32ncurses5 holotz-castle-data
  python3.2-minimal fb-music-high ttf-unfonts-extra lib32tinfo5 ia32-libs
  libsvga1 libqt4-test:i386 libqt4-script:i386 libqt4-designer:i386
  libquicktime2 libqt4-network:i386 libpython3.2 libtar0 libavfilter2
  libncurses5-dev libboost-signals1.46.1 libboost-program-options1.46.1
  libportmidi0 libavdevice53 otf-freefont python3.2 libqt4-opengl:i386
  libc6-i386 lib32ffi6 lib32gcc1 libqt4-xmlpatterns:i386 lib32asound2
  ri-li-data ufoai-music libtinfo-dev libgdbm3:i386 libhal1 ufoai-common
  vlc-plugin-notify libxt-dev ttf-yofrankie liblzo2-2 libqt4-sql:i386
  libqt4-svg:i386 spring-common frozen-bubble-data ttf-tamil-fonts
  libxss1:i386 python-rabbyt lib32ncursesw5 armagetronad-common libqtgui4:i386
  libvdpau1 lib32z1 lib32stdc++6 libqt4-scripttools:i386 ufoai-data
  libboost-regex1.46.1 libaa1-dev freeglut3 libmng1:i386 vlc-plugin-pulse
  libfaac0 python-opengl libpng12-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

```

Well this does help alot. Sorry for my first post, rereading made me see how frantic and unclear it was. I shall clarify what happened.

I couldn't install gens/gs:i386 without it telling me:
"If you install gens/gs future updates will not include new items in The Ubuntu Desktop system set. Are you sure you want to continue?"
It listed "39 apps" :/ and I didn't want to lose those so I chose to be a smart **** and downloaded the deb and did this "sudo dpkg --force-architecture -i gensgs.deb"
Upon opening Software Centre it said about the software catalogue and I said I did want to fix which meant all those packages were removed.
Finally I tried to re-install the software I lost but it says I must remove the :i386 software I installed.

So really it's my own stupid fault. Seems I can either install as much :i386 software as I want and use that or ditch it all together and get my 64bit apps back. I didn't know about the whole multi-arch thing until now but be sure I won't forget.

I am going to uninstall the :i386 apps, run an autoremove and an update on the sources to clean things up and finally install all my software back.

Finally, as a solution to using gens and zsnes I am either going to try and compile from source into a usable deb OR (and more likely) just going to crack the deb open and install the files manually.

I still don't fully understand it but all this seemed such a mystery until the multiarch thing. Thanks so much guys.

---

