---
title: "Difference between net-install and live?"
date: 2009-11-29
forum: General Help
---

### Post by TruePurple on 2009-11-29
I guess life takes up more hard drive space (if installed on your hard drive and not a CD) but is faster? 

So does that mean that if you have plenty enough hard drive space live is just a better way to run ubuntu then net-install?

What are the advantages and disadvantages of both?

---

### Post by Leppie on 2009-11-29
Usually live refers to a system you can boot of cd/usb. If using a cd, changes to the operating system (like installing additional applications) are lost when rebooting or shutting down the system.

Net-install installs the system on your hard-drive and during installation checks for updates for certain packages. Changes to the system are permanent.

---

### Post by TruePurple on 2009-12-02
But live can also be installed on a hard drive, right? If installed on a hard drive, does it still forget settings? Are there other differences as well beyond what you describe?

Is the sole reason live is faster, is because it skips searching for updates?

I was told by someone in chat that if you install from a "live" CD, what is installed on your hard drive is also a "live" version. This makes no sense to me, is it true or hogwash?

---

### Post by Grenage on 2009-12-02
An install keeps files on your hard disk, they persist through a reboot; a live CD runs purely out of memory and the data on the CD.  Because CDROMs are horribly slow, live performance is generally terrible by comparison.

---

### Post by winotree on 2009-12-02
> **TruePurple said:**
> ....I was told by someone in chat that if you install from a "live" CD, what is installed on your hard drive is also a "live" version. This makes no sense to me, is it true or hogwash?
Yes, you've installed the live version however once installed to your HHD or SSD it's no longer live -- it's permanent; it's faster; it's persistent in that it remembers everything you've done or saved. And good for you in thinking that it didn't make sense....  :D

---

### Post by TruePurple on 2009-12-02
Man, it seems everthing I was told in chat was bogus. They must have been cruelly messing with me or something. What do I look for in chat to know someone actually has knowledge in the area and won't mess me around? Any particular names or something?

Is there a way/how might I set up a flash drive to run ubuntu installed (not 'live'), off it? (so that it boots from the flash drive)

On a related note but requiring completely different expertise, does writing over a flash drive over and over, like i assume a OS install would do from virtual ram and updates, wear it out especially fast? But just reading off a flash drive wouldn't wear it out, or wear it out very fast?

---

### Post by Leppie on 2009-12-03
Usually best places to look for reliable information are forums like this one.

Regarding a live usb stick, have a look at [this guide]("https://help.ubuntu.com/community/USB%20Installation%20Media").

Usually it's recommended not to use swap drives on usb sticks as they wear out quickly that way. Swap drives can have high volume accesses, but I think this is only for systems low on memory. My swap is hardly ever touched (I have 3gigs of ram installed, but have read other people stating the same for lower amounts of ram).

---

### Post by TruePurple on 2009-12-04
Does a flash drive wear out if your only reading off it?

Can I install ubuntu on my flash drive (**_NOT_ LIVE**) so that ubuntu boots from it? If so, could I assign another drive as my swap drive? Would I then avoid most of the wear out on the flash drive?

P.S. I have about 768 mb of ram, though win98 only recognizes part(384mb) of that ram. I assume linux would see the whole bunch though.

---

