---
title: "No Grip in Breezy?"
date: 2006-02-07
forum: General Help
---

### Post by hoosemon61 on 2006-02-07
I had hoary installed on a laptop that I've just been playing with and started using GRIP to rip CD's (ones I own) so I could listen to them on my MP3 player in the car (no skips).  

I upgraded to Breezy, and now I find the package manager doesn't have GRIP available.

I tried sound juicer, but it only does ogg, which won't play in my MP3 player, and I even installed KAudioCreator, which does MP3, but it can't find the MP3 encoder.  

I've done lots of searching on the forum and none of what I've found helps.  The package manager didn't have LAME listed anywhere, and no MP3 encoder for KAudioCreator.

I did find a cool tip for speeding up rips by setting DMA=1 though.

Any ideas?


Thanks

---

### Post by RAOF on 2006-02-07
You need to add the universe/multiverse (I forget which exactly) repositories to get LAME - check out the first link in my sig.

Secondly, you can get Sound-juicer to produce mp3's.  You need to get the gstreamer0.8-lame plugin (I'd recommend just getting the gstreamer0.8-plugins, gstreamer0.8-plugins-universe, & gstreamer0.8-plugins-multiverse packages).  Then you need to create a profile (like the cd-quality lossy one) which uses the lameenc plugin.  I can't tell you how to do that right now, this computer doesn't have sound-juicer on it.

---

### Post by hoosemon61 on 2006-02-07
Thanks, I found the respoitory settings in synaptic just as I got your answer.  I think I've got it now...

---

