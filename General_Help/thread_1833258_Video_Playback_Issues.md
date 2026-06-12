---
title: "Video Playback Issues"
date: 2011-08-25
forum: General Help
---

### Post by GPmatic on 2011-08-25
Hello, I have recently migrated from windows and I'm now using Xubuntu 11.04. It is a very pleasant distribution and I like it very much but there is something that keeps bugging me. I am having trouble playing certain kinds of videos, which is strange because I had no video playback issues at all when I was using windows. For instance I could watch HD videos without any glitches or anything with windows, now I have to resort to finding lower quality stuff. I have tried countless video players but none seem to solve the problem. But before I go any further I will list my system specs---->

Dell Dimension 2400
2.66GHz CPU
768 MB Ram
Intel(R) 82845G Graphics Controller
64MB Graphics Memory

Don't know if any of that helps but, if someone can help please do because I really do like xubuntu despite this rather huge draw back. Watching movies is a big hobby of mine now so any help will be greatly, significantly and monumentally appreciated.

---

### Post by Duncan Williams on 2011-08-25
My opinion is that you are underpowered for HD stuff.
You also need to make sure you are using latest video drivers (not open source) and have your windows manager and other stuff setup correctly to start getting maximum results from your graphics processor.

No direct-X in linux but correctly configured with a decent graphics processor and it is as good if not better than windows graphic capabilities.

---

### Post by GPmatic on 2011-08-25
> **Duncan Williams said:**
> My opinion is that you are underpowered for HD stuff.
You also need to make sure you are using latest video drivers (not open source) and have your windows manager and other stuff setup correctly to start getting maximum results from your graphics processor.

No direct-X in linux but correctly configured with a decent graphics processor and it is as good if not better than windows graphic capabilities.
Thank you for your help sir. When you say underpowered do you mean I need more RAM, or a better graphic card? and how would I go about getting drivers?. I'm new to this kind of environment you know so I'm a bit lost O_O

---

### Post by Duncan Williams on 2011-08-26
another gig of ram would help.
The main issue with fast 3D and high definition graphics in linux seems to be.

Having a graphics processor that is fully supported, has say at least 512mb of video ram, Maintaining that the video ram is actually being used (and correctly)

It is not complicated but a lot of people are just touching the surface of there graphic capability by using provided open-source drivers or incorrectly configured proprietory drivers.

I am presuming from the specs you listed that you are using a desktop computer (not laptop).

The easiest and cheapest way to get a good graphics response:

Upgrade your ram to 1.768 gig(or replace your memory sticks with 1,2or 4 gig)

I would suggest a cheap nvidia card for graphics - the one I am using is very fast and well supported in ubuntu - nvidia geforce 6200 with 512mb vram (1 gig vram version even better) this is based on the nvidia 6800 series and uses nvidia current drivers (vers 280 available from x-swat ppa - vers 270 as standard in repository)
In Australia the card is about $40 new (which is very cheap)

Any more info required, please post back.

This post I made awhile back might be of interest to you:
[http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222](http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222)

note, if you have built-in graphics you will need to switch them off in bios before setting up the card.

---

### Post by GPmatic on 2011-08-26
> **Duncan Williams said:**
> another gig of ram would help.
The main issue with fast 3D and high definition graphics in linux seems to be.

Having a graphics processor that is fully supported, has say at least 512mb of video ram, Maintaining that the video ram is actually being used (and correctly)

It is not complicated but a lot of people are just touching the surface of there graphic capability by using provided open-source drivers or incorrectly configured proprietory drivers.

I am presuming from the specs you listed that you are using a desktop computer (not laptop).

The easiest and cheapest way to get a good graphics response:

Upgrade your ram to 1.768 gig(or replace your memory sticks with 1,2or 4 gig)

I would suggest a cheap nvidia card for graphics - the one I am using is very fast and well supported in ubuntu - nvidia geforce 6200 with 512mb vram (1 gig vram version even better) this is based on the nvidia 6800 series and uses nvidia current drivers (vers 280 available from x-swat ppa - vers 270 as standard in repository)
In Australia the card is about $40 new (which is very cheap)

Any more info required, please post back.

This post I made awhile back might be of interest to you:
[http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222](http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222)

note, if you have built-in graphics you will need to switch them off in bios before setting up the card.
I was planning to add another gig of memory for a while now so that's not an issue. The graphics card on the other hand will have to wait. I don't know if the link you gave me helped but I read the post carefully, thanks alot. 

One last question though, is Peppermint OS 2 a better alternative to Xubuntu 11.04?

I have been doing some reading on Peppermint and I'd like to try it. Again, thank you for your help, greatly appreciated.

---

### Post by Duncan Williams on 2011-08-26
peppermint is a lot faster and I personally prefer it for many reasons.
It is actually designed for older computers with less specs.

I would say yes, use peppermint 2.

more info:

[http://peppermintos.com/](http://peppermintos.com/)

[http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/](http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/)

[http://www.linuxdistroreview.com/peppermint-os-ice](http://www.linuxdistroreview.com/peppermint-os-ice)

---

### Post by GPmatic on 2011-08-26
> **Duncan Williams said:**
> peppermint is a lot faster and I personally prefer it for many reasons.
It is actually designed for older computers with less specs.

I would say yes, use peppermint 2.

more info:

[http://peppermintos.com/](http://peppermintos.com/)

[http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/](http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/)

[http://www.linuxdistroreview.com/peppermint-os-ice](http://www.linuxdistroreview.com/peppermint-os-ice)
Much thanks, will try Peppermint for sure. I don't think i'll be needing any help for a while but I'll be sure to ask if I ever do.

---

### Post by GPmatic on 2011-08-26
> **Duncan Williams said:**
> peppermint is a lot faster and I personally prefer it for many reasons.
It is actually designed for older computers with less specs.

I would say yes, use peppermint 2.

more info:

[http://peppermintos.com/](http://peppermintos.com/)

[http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/](http://www.linuxuser.co.uk/reviews/peppermint-os-two-review/)

[http://www.linuxdistroreview.com/peppermint-os-ice](http://www.linuxdistroreview.com/peppermint-os-ice)
Much thanks, will try Peppermint for sure. I don't think i'll be needing any help for a while but I'll be sure to ask if I ever do.

---

