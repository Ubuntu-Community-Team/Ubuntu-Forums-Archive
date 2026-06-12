---
title: "Movies Won't Play, Need Urgent Help"
date: 2009-10-07
forum: General Help
---

### Post by Prominence on 2009-10-07
I'm on Ubuntu 9.10 64 bit and a majority of my movies will not play, it won't show anything at all, or it'll say "Internal Stream Error" and on my Ubuntu 9.10 32 bit laptop, it all plays fine, what's causing this? 

I have a party coming up tomorrow night and I kinda need the movies for it...so it would be very very very very appreciated for someone were to help out.

Music plays fine, Movies Won't, if that helps any

---

### Post by Chronon on 2009-10-07
Just a guess, but did you install non-free-codecs?

---

### Post by Prominence on 2009-10-07
Didn't, but I just did, and no change

UPDATE: In VLC the Audio will play, but no video

No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "avc1". Unfortunately there is no way for you to fix this.

That's what it says

---

### Post by razorboy5 on 2009-10-07
same this is just a guess also but do u have the restricted extras installed?

i remember i needed those to play dvds

---

### Post by Prominence on 2009-10-07
Yeah, it's installed as well

Does the VLC info help any?

---

### Post by Chronon on 2009-10-08
VLC claims that it simply doesn't have the codecs. VLC uses its own codecs rather than gstreamer, so not installing non-free-codecs shouldn't affect anything in that case (AFAIK). 

I found a discussion on the VideoLAN forums about the same problem that you're reporting: [http://forum.videolan.org/viewtopic.php?f=13&t=65928](http://forum.videolan.org/viewtopic.php?f=13&t=65928)

It ends up pointing back to this topic: [http://ubuntuforums.org/showthread.php?t=1281367](http://ubuntuforums.org/showthread.php?t=1281367)

To save you the click, in case it isn't your problem, the ubuntuforums thread is about installation of Openshot breaking playback for VLC and Totem.

---

### Post by Prominence on 2009-10-08
Alright, that's my issue but how do I fix it all

---

### Post by Chronon on 2009-10-08
Doesn't the second post in that thread give instructions on how to fix it?

---

