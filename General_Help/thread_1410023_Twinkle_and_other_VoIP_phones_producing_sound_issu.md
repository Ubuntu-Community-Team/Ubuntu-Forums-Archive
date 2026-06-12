---
title: "Twinkle and other VoIP phones producing sound issues on LTSP"
date: 2010-02-18
forum: General Help
---

### Post by Anivair on 2010-02-18
I am currently running LTSP on a 64 bit ubuntu 9.10 server (installed with arch i386 because that's what my thin clients want).  

I can get SIP phones (twinkle, specifically) to run just fine.  It makes calls, but I get no sound at first on a thin client (works just fine on the server). 

In both places (same login) twinkle things it's using alsa for the sound (which does not seem to be the case, since I don't think alsa is even running). 

If I alter the sound settings for mono instead of stereo sound I get stuttering sound.  If I then open up the sound properties, the sound works perfectly, but will eventually revert back to stuttering.  

I really could use some assistance, here.

---

