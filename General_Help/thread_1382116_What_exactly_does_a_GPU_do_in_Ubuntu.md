---
title: "What exactly does a GPU do in Ubuntu?"
date: 2010-01-15
forum: General Help
---

### Post by ShakeyJake on 2010-01-15
Hey all.

I've been using a system with a 1GB 9500GT for a while now. It's by no means the most powerful of cards, but it still packs a hell of a punch and, best of all, it's completely passively cooled.

But what's the point? I mean VDPAU is great and all but normal video playback doesn't seem to use the GPU for anything other than connecting the pc to the monitors. The GIMP doesn't use it either (at least as far as I can tell) so what does a GPU do in linux???

I needed a card with two digital outputs to run dual monitors, and it pretty much had to be an NVidia one because I like nvidia-settings-manager. I wanted a pretty new one for VDPAU support too. But if, like most people, I had one screen and didn't care about HD, would there be any advantage of having something like a GTX295 over an integrated 6100 or something?


Cheers,
Jack

---

### Post by Mark Phelps on 2010-01-15
The CPU does NOT handle the video, that is done by a video chip.

Your video display is being handled by one of two GPUs.  If you have onboard video (a chip on your motherboard), IT is handling the video.  If you have an add-in card, the GPU on the card is handling the video.

So, if you're not using onboard video, then the GPU on your card IS handling the video.

---

### Post by falconindy on 2010-01-15
> **Mark Phelps said:**
> The CPU does NOT handle the video, that is done by a video chip.

Your video display is being handled by one of two GPUs.  If you have onboard video (a chip on your motherboard), IT is handling the video.  If you have an add-in card, the GPU on the card is handling the video.

So, if you're not using onboard video, then the GPU on your card IS handling the video.
Except that while the video card does the rendering, the CPU is still intimately involved in the decoding aspect of playing a video. The whole idea of an API like VDPAU is that you pass off the decoding aspect of the operation to the GPU.

OP: VDPAU is still a relatively new beast. If you only think you're using it and haven't gone out of your way to make sure that you are, chances are you aren't. My Core2DUo (3.16ghz) used to sit at about 15-20% load while playing back h.264 video (matroska container) pre-vdpau. Once I started using vdpau for my output as well as vdpau enabled codecs, my cpu usage dropped to roughly 5% playing the same video. Clearly, my video card was really working now.

As far as normal video playback and GIMP, video cards remain relatively untaxed in Linux.

---

### Post by lavinog on 2010-01-15
The gpu can have many proprietary features that cannot be used in linux.

gimp is making a transition to GEGL which is supposed to utilize the gpu for some tasks.

---

### Post by blur xc on 2010-01-15
What about stuff like Compiz or Google Earth?  How much of that is done by the gpu?  Are Flash videos, animations, games, etc..., rendered by the cpu or does the gpu jump in and help some?

BM

---

### Post by ShakeyJake on 2010-01-15
@Falconindy: I guess I should clarify. I know the GPU is accelerating playback with VDPAU. I configured mplayer to run VDPAU no problems and saw my CPU use drop to idling and scaled down to 800MHz/Core. By 'normal video playback' I meant just using a standard .avi in something like Totem or VLC. It really does seem like the CPU is doing most of the work in that instance.

@Mark: I think you may have misunderstood my question. I know the card is technically 'handling' the video. But like I said, it seems it's function is literally to connect the monitors to the tower. Under normal use (watching an .avi, editing photos etc) the CPU is doing all of the heavy lifting and the GPU is idling. Perhaps my question should be restated:

*What situations/programs utilize the GPU for video playback, image rendering, desktop effects and other uses? It seems that most of these functions (which should be performed by a graphics card) are actually being performed my the CPU.*

I'd be interested to see the answer to blur's question actually.

---

### Post by blur xc on 2010-01-15
Well, I'll add a couple more questions in there-

I have my conky monitoring my cpu and ram usage, is there a way to monitor gpu usage and vid card ram usage???

I have a modest but most likely overkill for my uses, Nvidia 9600 gt 512mb card.  Right now my conky only monitors gpu temp...

BM

---

### Post by gradinaruvasile on 2010-01-15
Compiz (composited desktop effects), Google Earth, and 3D games all use OpenGl hardware-accelerated rendering - on newer Nvidias VDPAU is used for hardware-accelerated video decoding. Also, Flash player should use it at least on Nvidia cards AFAIK - nonetheless it still has high CPU usage, but on Windows too has this kind of issues.

---

