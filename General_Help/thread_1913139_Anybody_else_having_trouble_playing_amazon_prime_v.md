---
title: "Anybody else having trouble playing amazon prime videos?"
date: 2012-01-22
forum: General Help
---

### Post by justinjstark on 2012-01-22
I used to play amazon prime videos just fine.  Yesterday, it started to not work.  The video plays for 2 seconds and then alerts "Sorry we were unable to stream this video.  This is likely because your Flash Player needs to be updated."

I tried reinstalling the latest version of flash but it is still not working.  I called amazon support and they ran me around the same circles: reinstall flash, restart the computer, try a different browser, etc.  After not reaching a solution, I was told they are escalating the issue and will call me back next week.

I'm wondering if anybody else has the same issue?  Maybe there was an OS update that broke something.  Maybe amazon updated their player and it is no longer working with linux flash.  I would like to solve this problem so I can get back to streaming movies/shows on my ubuntu machine.  I am using Ubuntu 10.04 with the latest chrome and firefox.

---

### Post by Paulr-55 on 2012-01-23
I too am experiencing this with Amazon streaming. On Ubuntu 11.10 and Debian Squeeze with Iceweasel Firefox & Chrome browsers. It worked fine for my 30 day trial, then I plunked down my 79 bucks and it breaks the next day.

I have found some instances where a video will play, which tells me it's Amazon's screw-up and not a Flash issue.

I get a "updating player" message then the error dialog. On the videos I have been able to get to work, no "updating player" message appeared.

---

### Post by Super R on 2012-01-23
Same problem here. I spoke to an Amazon representative and he said he will get back to me asap. I will post any answers I receive. I hope Amazon is not going the "We don't support Linux" route. 

They have the URL to this post, so please post if you are having problems so they can have as much info as possible.

---

### Post by justinjstark on 2012-01-23
The video plays for me for about 2 seconds before it stops and errors.  Maybe the problem has to do with the DRM and an issue between the linux version of flash and the amazon implementation!?

---

### Post by Super R on 2012-01-23
Just spoke to the Amazon rep again. He looked up some info and said it is a known problem and they are working on it. He said he will be contacting me with updates and I will post here when I know something new. 

FYI, mine originally played a couple of seconds then error, but now it just pops the error message after "Connecting".

---

### Post by justinjstark on 2012-01-23
> **Super R said:**
> Just spoke to the Amazon rep again. He looked up some info and said it is a known problem and they are working on it. He said he will be contacting me with updates and I will post here when I know something new. 

FYI, mine originally played a couple of seconds then error, but now it just pops the error message after "Connecting".

Yay.  You've gotten much farther with customer service than I was able to.  I'm glad this is being fixed.  :D

---

### Post by Frogs Hair on 2012-01-23
I'm able to play trailers with Opera . The trailers may not be long enough to reproduce the error though .

---

### Post by tobydeemer on 2012-01-25
I also have experienced this issue on any 11.10 system. The flash installer from medibuntu repos has the problem. 

Oddly, I tested a linux Mint Debian installation. It also experienced the issue, but after installing Flash-Aid addon for firefox, the Mint installation now works. This is true for a second Mint Debian install I tested on different hardware.

Flash-Aid for Ubuntu 11.10 did not work however, on two different installations. 

So far, this thread is the only hit I've seen of this issue. Be a real shame if I had to cancel Prime account for this... *sigh*

---

### Post by justinjstark on 2012-01-27
I've tried installing a few different versions of flash but none of them are working.

---

### Post by tobydeemer on 2012-01-28
Just another note- playback works without issue on the HD cotent- no error or player update message, etc. Non-HD TV episodes or movies experience the problem.

---

### Post by starchaser1 on 2012-01-28
Finally got a fix for my system.
from [amazon.com/forumspost]("http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_pg_next?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=2&cdSort=oldest&cdThread=TxFTGOK5LRL3JM")


From what Andy D Lim says

open terminal and run:

sudo apt-get install libhal1
sudo apt-get install hal

restart browser

works for me. :-)

---

### Post by Duplin on 2012-01-28
Many thanks starchaser1, that did it for me also, works great now.:-)

---

### Post by shevin on 2012-03-23
> **starchaser1 said:**
> Finally got a fix for my system.
from [amazon.com/forumspost]("http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_pg_next?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdPage=2&cdSort=oldest&cdThread=TxFTGOK5LRL3JM")


From what Andy D Lim says

open terminal and run:

sudo apt-get install libhal1
sudo apt-get install hal

restart browser

works for me. :-)

that does NOT help me , I am using chrome on ubuntu 11.10

---

### Post by nerdy_kid on 2012-06-06
You need to delete ~/.adobe/Flash_Player  AFTER installing hal.  The amazon player will update, and everything will be pretty....

---

### Post by NertSkull on 2012-10-07
Thank you, this solved my problems as well.  Hooray

---

### Post by moriokasan on 2012-11-27
Thanks a lot! This also resolved my issue!

---

