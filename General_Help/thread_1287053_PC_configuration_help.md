---
title: "PC configuration help"
date: 2009-10-09
forum: General Help
---

### Post by arnab_das on 2009-10-09
I'm upgrading my PC to AMD Athlon x2 240 (2.8Ghz) and getting a 2GB RAM (800) and a biostar nvidia 8200 motherboard. are these good enough configurations to run beryl/compiz?

I was planning to get nvidia 9400GT 1GB, but was advised against it since I heard its performance wont really add much to 8200's onboard performance.

---

### Post by kanikilu on 2009-10-09
> **arnab_das said:**
> are these good enough configurations to run beryl/compiz? Yes.

I think any discrete graphics card will be better than onboard, but the 8200 will run compiz fine.

---

### Post by scragar on 2009-10-09
The graphics card is all that really matters, everything else is provided in most basic systems.

That graphics card didn't have good linux support(being slow and choppy) as of january, but reports from march tell of it being good enough to play some games at 40frames/sec, not brilliant, but it should be sufficient for most compiz features.

---

### Post by arnab_das on 2009-10-09
thanks for ur replies. i'm basically looking forward to using beryl and compiz for the time being. games isnt really my primary concern. is 8200 onboard good enough for a full scale beryl performance or does it "just" meet the basic system requirement?

btw is the processor configuration okay?

---

### Post by scragar on 2009-10-09
> **arnab_das said:**
> thanks for ur replies. i'm basically looking forward to using beryl and compiz for the time being. games isnt really my primary concern. is 8200 onboard good enough for a full scale beryl performance or does it "just" meet the basic system requirement?
I posted info from March, if the drivers have been fixes since then(and there are no complaints about it since april as far as my searches turned up) you should get full performance using compiz-fusion(which has replaced beryl and compiz).
> btw is the processor configuration okay?

I should hope so, that's the processor I'm using :o

---

### Post by arnab_das on 2009-10-10
woo hoo! compiz, avant and cairo dock (later uninstalled as i loved avant better) all work awesome on this motherboard without any glitches! love it!!!

and i didnt even need an external graphics card! and now i'm not even facing the freezing of images on flash videos in full screen mode.

however its disappointing to know that:
1. ubuntuzilla isnt really meant for 64 bit processors (why??? :( )
2. no flash versions for 64 bit
3. no firefox for 64 bit (this one baffled me, honest!)


and still cant figure out how to fix low audio volume problem for HDA nvidia ALSA mixer :(

---

### Post by NoaHall on 2009-10-10
Check out my sig for flash 64 bit.

---

### Post by nanotube on 2009-10-12
> **arnab_das said:**
> 
1. ubuntuzilla isnt really meant for 64 bit processors (why??? :( )


because ubuntuzilla installs the official mozilla build, and mozilla doesn't release 64bit builds. that said, the 32bit build will work, but you'll have to fiddle around a tiny bit to get some plugins working (see ubuntuzilla faq for details)

> 
2. no flash versions for 64 bit


yes there is 64bit flash. (but if using ubuntuzilla, you should be using 32bit flash to comport with the 32bit mozilla build)

> 
3. no firefox for 64 bit (this one baffled me, honest!)


the major reason for lack of mozilla 64bit builds is that they're working on porting the tracemonkey javascript engine to 64bit arch, and until they're done, they won't make 64bit builds.  you can either grab the ubuntu repositories version, which work (but use the old js engine, presumably), or use 32bit build with ubuntuzilla.

> 
and still cant figure out how to fix low audio volume problem for HDA nvidia ALSA mixer :(

can't help you on that one...

---

### Post by arnab_das on 2009-10-13
> **nanotube said:**
> because ubuntuzilla installs the official mozilla build, and mozilla doesn't release 64bit builds. that said, the 32bit build will work, but you'll have to fiddle around a tiny bit to get some plugins working (see ubuntuzilla faq for details)



yes there is 64bit flash. (but if using ubuntuzilla, you should be using 32bit flash to comport with the 32bit mozilla build)



the major reason for lack of mozilla 64bit builds is that they're working on porting the tracemonkey javascript engine to 64bit arch, and until they're done, they won't make 64bit builds.  you can either grab the ubuntu repositories version, which work (but use the old js engine, presumably), or use 32bit build with ubuntuzilla.



can't help you on that one...

thanks for the info.
btw, if i download shiretoko browser (apparently thats firefox 3.5 isnt it?) what will happen to it when finally i upgrade to karmic? i heard that karmic has the 3.5 version.

---

### Post by nanotube on 2009-10-13
> **arnab_das said:**
> thanks for the info.
btw, if i download shiretoko browser (apparently thats firefox 3.5 isnt it?) what will happen to it when finally i upgrade to karmic? i heard that karmic has the 3.5 version.

presumably it will be replaced with the ff3.5 that's in the karmic repos.

---

### Post by arnab_das on 2009-10-14
btw the low audio volume has been fixed. i typed "alsamixer" from the terminal and changed the "front" volume and everything's working fine! :)

---

