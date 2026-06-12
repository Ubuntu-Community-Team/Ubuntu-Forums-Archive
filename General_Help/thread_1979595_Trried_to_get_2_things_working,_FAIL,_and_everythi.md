---
title: "Trried to get 2 things working, FAIL, and everything else broke."
date: 2012-05-13
forum: General Help
---

### Post by mdocod on 2012-05-13
Hello,

I'm running 10.10 if that means anything. 

So I had 2 goals in mind. 

A: get Windows file sharing (samba) installed, configured, and working so that I can share the media on my desktop with the various laptops in the house. 

B: get Rythmbox to recognise my old iPod shuffle. 

I used synaptic to install samba and various other related packages. Tried 2 GUI configuration tools, no success with either. The result of this attempt seems to be that the X window system no longer fires up automatically. How these things could be even remotely related, is beyond my comprehension but yes, I am claiming that an attempt to install samba screwed up system configuration elsewhere. 

I read a few suggestions online for the iPod issue, mostly to update the various pieces of software related to the recognition of ipods and other devices. I also "gave in" and hit "mark all upgrades" to update the system. I had previously had the preference set to "prefer installed version" but had to switch that to "prefer latest" to get the later versions of the software that was "supposed" to fix the ipod recognition. After this "update," compiz has gone bonkers, pretty much always using an entire CPU core, and occasionally the whole screen just goes black for a few seconds, and for some reason, glmatrix, my screen saver, now runs "in the background" using up a full core of it's own. Force quitting glmatrix doesn't really help, because it just comes back after about a minute on it's own. 

I can't believe I broke my rule for this install. I remember telling myself to get it stable and leave it the heck alone. No, I just couldn't resist updating, the surefire way to break linux every time. Updates have more often been the reason I've had to reinstall this OS more than anything "I" have ever done. Bah!

Any easy ways to get the auto-login and x window system on boot back, and some sort of prosac for compiz? At this point I don't care if file sharing never works and my ipod never is recognised, I'd just like the system to get back to running stable. Right now it's a mess.

Thank You and Regards,
Eric

---

### Post by Mark S Bilk on 2012-05-15
> **mdocod said:**
> 
Hello,

I'm running 10.10 if that means anything.  So I had 2 goals in mind.

A: get Windows file sharing (samba) installed, configured, and working so that I can share the media on my desktop with the various laptops in the house.

B: get Rythmbox to recognise my old iPod shuffle.

I used synaptic to install samba and various other related packages. Tried 2 GUI configuration tools, no success with either. The result of this attempt seems to be that the X window system no longer fires up automatically.

I read a few suggestions online for the iPod issue,... After this "update," compiz has gone bonkers, pretty much always using an entire CPU core, ...
occasionally the whole screen just goes black for a few seconds, glmatrix, my screen saver, now runs "in the background" using up a full core of it's own.

Thank You and Regards,
Eric


It seems the upgrades may have produced a mix of old and new packages
that are incompatible.

Suggest you back up all your personal (home) files onto another disk,
and do a clean install (not an update) to the most recent version of
Ubuntu that's been out long enough to be completely bug-free --
11.10 Oneiric Ocelot.  A year more recent than the version you were
using, the samba and ipod facilities that come with it "out of the box"
will probably do what you want without any further updates.

You should be able to get back into your system by using the 11.10
"live CD".  Partition a separate hard drive and copy your home files
onto it.  Check those files, exit normally, turn off the power, and 
disconnect the backup drive so that nothing can possibly happen to 
your saved data.

Then go back in with the live CD and totally clean out the system
partition of your original drive so you can get a clean install 
of 11.10.  One way to do this is to remake the filesystem in that 
partition (presumably ext3 or ext4).

Then do your clean install of 11.10, copy your backed-up files into your
home directory (if they aren't still there), and you should be good to go.

I've used Linux for the last 11 years, but not Ubuntu yet.  So you might
run these suggestions past the folks in the IRC channel first -- #ubuntu in
irc.freenode.org. 

Good luck!

---

