---
title: "DVDs play but at like double speed!?!"
date: 2006-04-16
forum: General Help
---

### Post by rainbowjoshua on 2006-04-16
So, on my freshly installed Breezy system (MSI RS480 motherboard), I rain automatix and installed about everything (which worked perfectly before I sent my motherboard in for RMA), and now DVDs play, but they do it SUPER FAST, like double or triple speed.  

Obviously quite unwatchable... any help would be quite appreciated!

Thank you!
Joshua

---

### Post by graigsmith on 2006-04-16
hmm wierd, is everything else working at the correct speed?  your system clock? cd playback? mp3 or ogg file playback?   what about if you use totem to play a random video?

---

### Post by rainbowjoshua on 2006-04-16
Actually, everything was going super fast... and when I posted that, the ubuntu forums brought me some "similar posts" and low and behold, there was the solution to my problem!  Working great now, the solution was:

noapic acpi=off

Thanks!

---

