---
title: "Next version of Ubuntu updater, and dial-up"
date: 2010-02-21
forum: General Help
---

### Post by Bartender on 2010-02-21
Good morning!
The other day I read that the next version of Ubuntu will roll Update Manager, Synaptic, etc. all into the Ubuntu Store.

I've just recently started using the Package Download Script (PDS) tool in Synaptic to get updates for our dial-up desktop PC via a laptop and broadband in town.  Does anyone know whether the Package Download Script will still be available after everything's been incorporated into Ubuntu Store?  Without that tool I'm screwed.

It's been great to finally be using Ubuntu at home behind our dial-up connection.  If PDS disappears I'll have to go back to XP and that would suck.

---

### Post by Pollox on 2010-02-22
I think we are still a ways away from the Ubuntu Store incorporating the features of all those programs (it's not there yet in the development version).  Even when it does get there, who knows if Synaptic will still be included by default or not also.  You could always install Synaptic if at any point it is no longer on the default Ubuntu image.

---

### Post by _duncan_ on 2010-02-24
Are both computers using the same version of Ubuntu?

If so, using PDS seems like an unnecessary step since most (if not all) of the update .deb packages are already in the /var/cache/apt/archives folder of the laptop.

It's just a matter of copying all these .deb files into the /var/cache/apt/archives folder of the dial-up PC by whatever means is most convenient for you, then proceed to update the system as usual. Ubuntu will "see" these .deb packages and no longer download from the repos.

There is an off-chance that some packages needed by your PC but not present in the laptop may need to be downloaded, but these are probably going to be quite small and your dial-up connection ought to be able to finish the update for you.

---

### Post by Bartender on 2010-02-26
Hi, duncan -

I've been afraid to try what you suggest.  I've added several PPA's to the laptop, which is the machine I use to get the packages, and I don't know if that could cause something to go sideways.  Once I convince myself that I might screw things up, it's hard to talk myself out of it. 

The laptop's running Jaunty.  One of the desktop PC's stuck at home is also running Jaunty, the other's running Karmic.

I imagine I'll move everything to 10.4 at some point, but have invested so many hours at the library installing PPA's and etc. to the lappy that I don't relish the thought of starting over.

As if dial-up wasn't already too much fun for one person, our library's wi-fi slowed way down recently.  Used to be able to download a Linux .iso in about an hour, watch videos easily, Ubuntu updates would clip along at about 700+ kb/s.  Now videos are unwatchable and updates run at about 30 kb/s.  I don't know what's going on, but I've been emailing the library IT guys with Speedtest.net results, hoping they'll spend some time figuring out what's wrong.

---

### Post by _duncan_ on 2010-02-27
The process isn't likely to cause any trouble with the lappy since you are only copying files from it and not making any changes to the system. The deb files from the PPA will be copied along with the other deb files from the laptop to the desktop, where it will remain unused if the desktop is not subscribed to the same PPA.

My advise is to go with what you're comfortable with. If Lucid Lynx comes along and the lack of PDS really becomes a problem, rest assured that there are various ways to go around it. After all, the script created by the PDS is nothing more than a series of wget statements to fetch the appropriate packages from the repo. Nothing that a little tinkering with apt and a text editor cannot replicate.

Hmmm, maybe my echo will read this and post a step-by-step on the dial-up thread.:D

---

