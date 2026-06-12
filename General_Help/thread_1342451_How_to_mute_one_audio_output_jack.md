---
title: "How to mute one audio output jack?"
date: 2009-11-30
forum: General Help
---

### Post by Dr. Oddbio on 2009-11-30
Is there a way to mute one of my audio jacks? I like to keep my speakers plugged into one, but I want it to get muted when I plug headphones into the front audio plug.
Although this is done automatically on my windows partition, I really don't mind at all just doing this manually.
But I really want at least some way to do it.

Any advice?
Thanks

---

### Post by fluffman86 on 2009-11-30
I was under the impression it happened automatically.  But if it doesn't, open a terminal and run "alsamixer".  You can press "M" to mute, and use the arrow keys to move left and right to different devices and up and down to adjust volume.  "Q" will quit the program.

---

### Post by Dr. Oddbio on 2009-11-30
Well it is a little odd.

When I go to alsamixer, I see the Headphones part but I cannot increase it, it doesn't have a bar, just an MM at the bottom.
But changing the "front" volume changes the volume for both the speakers and the headphones.

Also, just to include a little more info, when I plug in the headphones to the front instead into my speakers I can hear the same audio through **both** my speakers and my headphones.

The way my system is set up, I don't think there is a distinction, so I don't think it would do it automatically. What I mean is that I have two audio outputs, one front and one rear, they are essentially the same thing, but I have my speakers plugged into the rear jack, so naturally I would want to mute them when I plug my headphones into the front. As of now I'm just plugging them into my speakers but it's a little inconvenient for me.

---

