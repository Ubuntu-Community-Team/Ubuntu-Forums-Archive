---
title: "installed, sound wouldn't work.  Reinstalling"
date: 2009-12-08
forum: General Help
---

### Post by brhokla on 2009-12-08
I have a HP DV4 series laptop with AMD dual core turion 2.2, 4 gigs ram.  I installed Ubuntu 9.10 and all was great but the sound problems.  should I try 9.04 or maybe Kubuntu or what?  Any advice?  I couldn't get the sound to work and it was driving me crazy.

---

### Post by LuisGMarine on 2009-12-08
Open up terminal and type this into the command line, post back the results:  

```
aplay -l
```

There is no point of re-installing.  Try and figure out what your problem is first =) :popcorn:

---

### Post by lidex on 2009-12-08
What steps, if any, have you taken? 
Enter this command in a terminal (accessories>terminal):
```
alsamixer
```
Make sure your levels are up/unmuted especially master, pcm, front.
And please follow LuisGMarine instructions. :wink:

---

