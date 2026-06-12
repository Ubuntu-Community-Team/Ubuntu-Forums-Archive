---
title: "Errors in Totem..."
date: 2006-02-12
forum: General Help
---

### Post by BitTorrentBuddha on 2006-02-12
Ok, I was trying to watch the IT crowd on totem, it's wmv, the video plays well, but the sound chirps in about half a second every minute or so and stays quiet the rest of the time, when I tried running it in terminal I got the following errors:```
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:305280  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   
Decoder is capable of YUV output (flags 0x1b)

```
any ideas?

---

### Post by stoswald on 2006-02-12
I have the same problem, also it seems some windows media files don't have any sound at all and I tried a .MOV file which would start fine but after about 10 seconds the sound dissapears completely. I have tried a DVD which played fine with sound. I have installed Totem-Xine and the recomended Libraries anyone else having similar troubles?

---

### Post by SavageBeginner on 2006-02-12
I had the same problem, and this fixed it.
In terminal:
```
gedit ~/.xine/catalog.cache
```Search the file for 'w32dll.so'.  A few lines under each one you'll see 'decoder_priority=1'. Change it from 1 to 7 and save.  That should solve the problem.

---

### Post by BitTorrentBuddha on 2006-02-12
Don't know what it did, but it worked, thanks so much, I'm finally free of mplayer now.:D

---

### Post by The Mekon on 2006-02-12
Amazing I had this problem 10 minutes ago and I decided to give up and visit Ubuntu Forums instead.  The first thread I look at has solved it!

Thanks

---

### Post by stoswald on 2006-02-12
OOOOH YEAH 
finally that one had me stumped for a couple days now round of applause for savage beginner. Where did you find out about this fix is it documented somewhere because it seems to be a common problem.

---

### Post by SavageBeginner on 2006-02-13
I don't know of any documentation.  I found this on some other forum a while ago.  Sorry, I don't remember where it was.

---

### Post by sunny_nwho on 2006-02-20
Absolutely gr8 thank u very much

---

### Post by dude of wonders on 2006-02-26
[QUOTE=The Mekon]Amazing I had this problem 10 minutes ago and I decided to give up and visit Ubuntu Forums instead.  The first thread I look at has solved it!

Thanks[/QUOTE]
^^^ yep but 2nd thread i looked at, gotta love the help these forums give.

same problem here and same show "ITcrowd" :) awesome i thought it would of been something harder to fix but just simply changing 1 to 7 did it :mrgreen:

---

### Post by BigRod on 2006-04-12
Am I the only person who this didn't work for?  In both totem and xine I get crazy chop-tastic sound and when I try to play videos in mozilla they play for like 2 seconds with no sound and then stop.  Any ideas?

---

### Post by BitTorrentBuddha on 2006-04-12
Mine doesn't have any sound at all for the firefox plugin, I was referring to the actual application.

---

### Post by Corvair on 2006-05-15
Thanks to SavageBeginner for the wonderfull tip on Totem sound. Works OK now.:D

---

