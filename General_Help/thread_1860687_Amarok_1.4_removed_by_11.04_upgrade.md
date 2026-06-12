---
title: "Amarok 1.4 removed by 11.04 upgrade"
date: 2011-10-15
forum: General Help
---

### Post by Mooseknuckle on 2011-10-15
Hello!!

My favorite app just got nuked for no apparent good reason ... how do I get it back?

I just upgraded to 11.04, and noticed that it uninstalled my custom version of Amarok 1.4, and its supporting libraries.   None of the google results for getting it installed back seem to work ... There was a custom ppa which doesn't seem to be working anymore.   

Please don't tell me to use Amarok 2.*, or to try Clementine.   I want my Amarok 1.4 back :)

---

### Post by mc4man on 2011-10-15
Was thinking about that last night when I was putting totem-xine on a 11.10 install. (I think 11.10 may finally be the end of the road for that.

Haven't built amarok 1.4 since maverick, was wondering if it was still viable. (or even the pana redo
May give it a try this weekend, if any luck will let you know..

---

### Post by DemonSharkKisame on 2011-10-15
Amarok 1.4, as well as KDE3 in general, has been absorbed by the Trinity team. [http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)
While they don't have anything for Oneiric yet, they are working on getting 11.10 binaries out by late October/early November. Hope this info is of use to you! :D

---

### Post by mc4man on 2011-10-15
> **DemonSharkKisame said:**
> Amarok 1.4, as well as KDE3 in general, has been absorbed by the Trinity team. [http://www.trinitydesktop.org/](http://www.trinitydesktop.org/)
While they don't have anything for Oneiric yet, they are working on getting 11.10 binaries out by late October/early November. Hope this info is of use to you! :D
Thanks - That may be something to look at - 

Taking a quick glance at the current build-deps for 1.4.10 - while 11.04 looks ok to do, 11.10 may be a bit of an issue for some of the kdelibs (needs some kdelibs4 which aren't in 11.10, adding natty versions may not be worth the hassle

Edit; - can't see doing on 11.10 unless amarok can use the kdelibs5 which is doubtful

---

### Post by mc4man on 2011-10-15
After several hrs did get a working amarok-1.4 on 11.10
Though now need to check if I managed to bork anything on the install, ect.
Disabled some things to just simplify getting a good configure & build
(were some linking issues, a bad header & some gcc issues.

Seems to run fine as a music player (all i've tested), & the systray icon could use some help - needs a transparent background - this I don;t know how to fix.

---

### Post by mc4man on 2011-10-17
Spent a little more time on - fairly straightforward but does involve installing 8 - 11 packages from natty or maverick

Not sure if anyone would/could ppa it because of this, but certainly can be locally built & other than the less than ideal systray icon seems ok.

---

### Post by Kadai on 2011-10-17
I'm really looking forward to this.

And, what packages are actually needed to get this done? While I may not be sure of there can be a PPA set for merely this Amarok hack (but sure is possible to some extent as logn it does not break the KDE packages), I swear that there are many people that actually are holding back its breaths just to find out how to get Amarok 1.4 back.

Other of the alternatives (so far) is to move then to other players like Clementine (that is excelent, but it lacks a proper iPod support...) or even Guayadeque (but this one does not recognize my iPod on Kubuntu 11.10)... but I really want Amarok1.4 until a mature alternative is around.

By the way, props by the effort!

---

### Post by mc4man on 2011-10-17
This is the current successful conf & build though debating on the 2 marked in blue, myself probably don't need
The mp4 required an add. 4 older packages no longer used in 11.10 - the mysql 3 add., though I didn't try yet with 11.10's versions which may be ok

==========================
 ===  Amarok - PLUGINS  ========================================================
 ==========================
 =
 = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - yauap-engine
 =   - Postgresql Support
 =   - Konqueror Sidebar
 =   - Creative Nomad Jukebox Support
 =   - MTP Device Support
 =   - Rio Karma Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + libvisual Support
 =   [COLOR="Blue"]+ MySql Support[/COLOR]
 =   + MusicBrainz Support
 =   [COLOR="Blue"]+ MP4/AAC Tag Write Support[/COLOR]
 =   + iPod Support
 =   + iRiver iFP Support
 =   + DAAP Music Sharing Support

haven't been able to test an ipod - had one lying around for several years to test with, somehow in 11.10 dev I bricked it but good. Still works but no Os see it anymore, not windows, mac, or linux

Also need for anyone wanting to build to come up with how to install the deps, shouldn't be too hard, more a list of what 11.10 packages to install first.

---

### Post by Kadai on 2011-10-19
I have myself an iPod on what I can test it on, even a MTP Device (a Sony Walkman)... the only thing is how to get this amarok thing running to test...

Now, I think the iPod will for sure work (Because it did on past versions, and it relies most on libgpod... if Amarok can see devices, then everything can work).

---

### Post by mc4man on 2011-10-19
> **Kadai said:**
> I have myself an iPod on what I can test it on, even a MTP Device (a Sony Walkman)... the only thing is how to get this amarok thing running to test...

Now, I think the iPod will for sure work (Because it did on past versions, and it relies most on libgpod... if Amarok can see devices, then everything can work).
I believe MTP is out - at least per my involvement

I can give you a pretty good semi-how  to tomorrow, I'll run it on a live session & make sure it works out with limited hassle, meaning eliminate possible broken packages

Are you on 32 or 64 bit install, I did this on 32 bit so that should be cool, if 64 bit hopefully no new issues.

---

### Post by Kadai on 2011-10-20
> **mc4man said:**
> I believe MTP is out - at least per my involvement

I can give you a pretty good semi-how  to tomorrow, I'll run it on a live session & make sure it works out with limited hassle, meaning eliminate possible broken packages

Are you on 32 or 64 bit install, I did this on 32 bit so that should be cool, if 64 bit hopefully no new issues.

I'm on a 64 bit system, but I can at least run 32 bits apps (because of the compatibility libraries). so then I do not mind a 32 bit program as long it is as good as amarok.

But then posting a step-by-step guide may help not only me, but all many that might be looking for a solution for this (Even that This is the only thread I have seen of Amarok1.4 so far for oneiric!), to then address some of the possible issues... and I wonder if it is possible to make it standalone at some point, or even have all dependencies and code at hand >.<

But maybe that might be too much.

---

### Post by mc4man on 2011-10-21
> **Kadai said:**
> I'm on a 64 bit system, but I can at least run 32 bits apps (because of the compatibility libraries). so then I do not mind a 32 bit program as long it is as good as amarok.

But then posting a step-by-step guide may help not only me, but all many that might be looking for a solution for this (Even that This is the only thread I have seen of Amarok1.4 so far for oneiric!), to then address some of the possible issues... and I wonder if it is possible to make it standalone at some point, or even have all dependencies and code at hand >.<

But maybe that might be too much.

A standalone would be a lot of work, not sure about

Anyway worked it out - only need 5 natty packages that aren't available in 11.10, the rest are all 11.10 versions & worked out a  build-dep list that will prevent broken packages when installing them.
(the advantage there is no package will be subject to being updated or have to be pinned

This will have to be built locally, it is possible to build in a clean env & provide a deb's, but that's not in the cards, at least from here.

Will post into this thread tomorrow a how to do on 11.10, am going to try a amd64 to see. There's no reason it shouldn't work though occasionally amd64 can have unique linking issue

[http://ubuntuforums.org/showthread.php?t=1559002&page=2](http://ubuntuforums.org/showthread.php?t=1559002&page=2)

Edit: I'm wondering if there is any advantage to - 
MP4/AAC Tag Write Support
It can be enabled but requires an additional 4 packages from natty, they where removed in 11.10

Re-edit: how-to for 11.10 in place in link above...

---

