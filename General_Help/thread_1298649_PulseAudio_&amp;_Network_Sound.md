---
title: "PulseAudio &amp; Network Sound"
date: 2009-10-23
forum: General Help
---

### Post by arrrghhh on 2009-10-23
Hey all, I'm trying to get PulseAudio to stream audio to other machines in the house, in sync.  I'm using MPD to play the music, and someone suggested using Pulse.  I quickly set it up, and it seemed very easy, but I can't seem to get it working now...

I was thinking multicast would be the best method, especially if I was going to add anymore machines to listen in.  I don't think there's anything blocking multicast on my LAN, but I can't get the audio to work at all on the other machine now!  It's connected to my network just fine, I can ping and ssh to the box without a problem...

So is there a good guide on PulseAudio and network streaming?  I've read several, the best one I found was actually on the Pulse wiki site... but I still don't understand what needs to be done to get multicast to work.  I read somewhere that it'll make for choppy audio, and I do have choppy audio on the local output, whenever the stream is being sent out, but nothing is connecting.  It used to go away (when the other computer would connect to the stream) but now it won't, unless I disable the network stream on the server.

I don't get how this was working, is now broken and the same method of setting it up doesn't work?  Any help/advice would be greatly appreciated, especially pertaining to multicast, as I'm pretty sure when it was working previously it was unicast only anyways...

Previously I just setup MPD to use a pulse stream to an IP... then use paprefs on the computer that was to pickup the stream, and enable access to local sound devices w/o authentication, etc.  It was very easy, but this same method is not working for me now for some strange reason.  Thank you!!

---

### Post by arrrghhh on 2009-10-26
Bump?

Someone suggested using JACK with a JACKNET plugin to stream the audio, but that seemed much more involved...

Just something that _works_ is good enough.  Obviously works well would be nice as well!!

I thought Pulse was my answer, perhaps it's not...

Is there a better method for streaming audio over my LAN?

---

### Post by TwoToneSpirit on 2009-12-14
I'm looking for an answer to this question also.  Perhaps we can help one another out?

---

### Post by arrrghhh on 2009-12-14
Well I use MPD because it's the best player I've found that runs headless with as many songs as I have, all while having readily clients available on every platform imaginable, with my favorite being the MPM plugin for Firefox.  Very nice.

My problem is how to get it to other rooms...  I'm thinking I may break down and shell out the $100 some odd dollars for a quality fm modulator.  Found a really nice one with insane reviews, but it's not cheap.  But it solves all my problems, plus adding more "clients" is stupid-easy.  Definitely not my first choice, but after thinking about it, does make the most sense.  Just be sure you get a high quality fm modulator.  The one I speak of is at [http://www.edmdesign.com/](http://www.edmdesign.com/), which is pretty pricey but I KNOW is high quality.  I found another for $99, that seemed like a much better deal, but I'm not sure or not of his reviews are bogus... This one is at [http://www.wholehousefmtransmitter.com/](http://www.wholehousefmtransmitter.com/).  It just seems more phoney-internet scheme style site than the edmdesign one, plus I know someone who has an edm one, and it is amazing.  Anyhoo, not really an Ubuntu solution, but a solution nonetheless.

---

