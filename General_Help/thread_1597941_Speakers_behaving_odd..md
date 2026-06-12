---
title: "Speakers behaving odd."
date: 2010-10-15
forum: General Help
---

### Post by Th3Professor on 2010-10-15
Hi, my speakers are behaving odd.

I watch or listen to something with headphones and the sound is fine.

I use the normal speakers and there's a very weird "pulsing" like effect going on.

It's not a pulsing sound but the actual normal sound is like it's pushing and pulling back and forth like several repeated nonstop fast volume up-down-up-down.

Or, at least, I don't notice it in the headphones but just the normal speakers, it might be in headphones too but not as bad. :confused: 

Anybody know what the cause might be or possible solution?

---

### Post by ellgor on 2010-10-16
Hi,

You don't say but I'm guessing you have PulseAudio as the sound server, I found this distorted playback and also affected the behaviour of other unrelated apps, I removed PulseAudio with:

sudo apt-get --purge remove pulseaudio

everything now defaults to Alsa, programs work correctly and the sound doesn't seem like its coming from the bottom of a bucket, this is my experience and the fix that works for me, hope it helps you.

Regards, Ellgor.

---

### Post by Th3Professor on 2010-10-28
I think the headphones issue was my imagination. I double-checked connections for headphones and all is fine w/ that. However, the normal speakers, they just stopped working. It's an old "2.1" Harmon Kardon set with the L+R powered by the subwoofer, which is plugged into the wall and it has it's own fuse... so, they all just stopped working, won't even turn on when plugged into different wall outlets. I'm wondering if it just needs a new fuse.

Does anybody know if a fuse for speakers is about to fizz out if that would cause a pulsing-type effect in sound before the fuse dies?

Hopefully that's all it'll take to fix the speakers/sound without having to use headphones all the time.

On the other hand, I'm looking into getting 7.1 speakers for when I build my HTPC tv/computer set-up. Any recommendations on 7.1 brands and particular models to consider?

Thanks!

---

### Post by Th3Professor on 2010-11-02
Anybody?

---

