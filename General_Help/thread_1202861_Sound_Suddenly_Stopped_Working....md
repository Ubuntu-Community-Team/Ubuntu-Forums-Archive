---
title: "Sound Suddenly Stopped Working..."
date: 2009-07-02
forum: General Help
---

### Post by Topher88 on 2009-07-02
Hi.  I've been using Ubuntu Jaunty for a few weeks now.  The sound had working fine, but yesterday it randomly quit.  I checked and everything is plugged in where it is supposed to be.  The only changes I made (that I can recall) was unzipping a .dll file so that Digsby would run properly in Wine and installing Miro.  I uninstalled Miro and it did not fix the problem.  Any suggestions?

---

### Post by Topher88 on 2009-07-02
Nothing?  This is driving me crazy!  I've tried switching cords, I've tried everything and I can't figure out why my sound suddenly stopped working!  Oh, I also ran updates yesterday, so maybe something in the scheduled updates messed up.  Please, any suggestions at all would be great...

---

### Post by tvtech on 2009-07-02
okay first of all this is likely a wine related issue.  Wine is something close to evil although not quite, I think it has something to do with what it's trying to emulate.

but do yourself a favor I'm assuming you have gstreamer installed. 

launch the following app  gstreamer-properties  in an app launcher. 

check and see if that works also check and see what device and what audio system/mixer your using.

---

### Post by Topher88 on 2009-07-02
nope, none of that worked...  I tried all the different settings in gstreamer and got no results.  It says "unsupported" under the device, but this baffles me because it's been working perfectly up until yesterday...  Could it possibly have anything to do with the updates?  Has anyone else been having peculiar sound problems since installing yesterdays updates?

I noticed in another thread that this happened to someone after they had to shut down their computer via holding down the power button...  I think I had to do that recently because it was acting up in some way or another, so could that be a contributor?  I'm just trying to locate the culprit, and it's driving me mad!

---

### Post by Topher88 on 2009-07-04
So...  Any new advice?

---

### Post by markharding557 on 2009-07-04
you said this problem started after updates so do you have an older kernel installed?try it
if not install one in synaptic(search linux-image) and choose an earlier version

---

### Post by Topher88 on 2009-07-05
Neither kernels 2.6.28-13 or 2.6.28-13 work correctly.  Might try more later...

---

### Post by Topher88 on 2009-07-05
Still no results, nothing I try is working.  Any more suggestions???

---

### Post by sdlynx on 2009-07-05
you've tried messing with your mixer settings?

---

### Post by Topher88 on 2009-07-05
> **sdlynx said:**
> you've tried messing with your mixer settings?

Most certainly.  Everything seems to be in place as far as I can tell; no mysterious mutings or suchlike.  Unless there is something more advanced I need to be looking for, the basics look as they should...

---

### Post by sdlynx on 2009-07-05
do you have the Intel HDA sound card..?

if so take a look at this, when I first installed Ubuntu on this new laptop I wasn't getting sound either and this fixed it: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by markharding557 on 2009-07-06
> **Topher88 said:**
> Neither kernels 2.6.28-13 or 2.6.28-13 work correctly.  Might try more later...
the oldest kernel i see in in synaptic is 2.6.28-11 you could try that

---

### Post by Topher88 on 2009-07-07
> **markharding557 said:**
> the oldest kernel i see in in synaptic is 2.6.28-11 you could try that

Yeah I've only tried the other one that shows up in grub so far.  I might give that a shot when I get home (I'm at work right now).  Question, though; if that works, then how do I install updates without effing up my sound???

And I'm pretty sure that I don't have the Intel sound card.

---

### Post by sdlynx on 2009-07-07
Its likely that your sound problem will be fixed in the next kernel.  You can install updates while still running the older kernel, as that only affects drivers (to my knowledge).

---

### Post by Topher88 on 2009-07-18
Okay, I've let this sit for a while because I haven't felt like really messing with it, but I'd like to jump back in now and see if I can't get this figured out.

One option appears to be rolling back to an older kernel; how would I do that?  Are there any risks that I should know about if I decide to go that route?  What exactly will change if I roll back?

Or is there ANYTHING at all I can do with the current kernel?  Could it have to do with driver failures or something of that nature, and how could I find out if that is the case?

Any and all help appreciated...

Thanks!

---

### Post by sdlynx on 2009-07-18
It is quite likely that you already have more than 1 kernel on your machine, and on grub it should show like "Ubuntu on linux-generic-2.8.13" or something like that, the top one is the kernel you are currently running, and the next one down is recovery, and finally the next latest kernel you have installed.  Basically pick the third option in GRUB and see if sound works then.

---

### Post by Topher88 on 2009-07-18
> **sdlynx said:**
> It is quite likely that you already have more than 1 kernel on your machine, and on grub it should show like "Ubuntu on linux-generic-2.8.13" or something like that, the top one is the kernel you are currently running, and the next one down is recovery, and finally the next latest kernel you have installed.  Basically pick the third option in GRUB and see if sound works then.

I've actually already tried that, and had no success.  I think it's on 13 now and I tried 11, and it didn't do me any good.  I might try it again just to make sure, but I'm pretty sure that that doesn't work.

---

### Post by Topher88 on 2009-07-18
Okay!  I got some sound to work!  It sounds like crap, but it works!  I changed back to the old kernel and messed with some sound settings in the "Preferences" section.  I don't know if the kernel switch had anything to do with it, but I'll see here in a little bit...

---

### Post by Topher88 on 2009-07-18
Alright, got it figured out...  Didn't have anything to do with the kernel, somehow some sound preferences got messed with, maybe because of updates or something else that tweaked the settings without my knowledge, and the DAC setting was muted so I had to check that and un-mute it, and then it sounded like crap because the PCM was all the way up and it was causing distortion, so I had to turn that down.  Like I said, I hadn't really decided to sit down and really mess with it until now, so...  Anyway, thanks for all the help.

---

