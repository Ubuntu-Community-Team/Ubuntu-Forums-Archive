---
title: "Rhythmbox &amp; Tuxguitar Problem..."
date: 2009-12-02
forum: General Help
---

### Post by marmotapl on 2009-12-02
Hello.

When I have both programs running, Rhythmbox 0.12.0 & Tuxguitar 1.1, I'm unable to use them at the same time... e.g. If i'm listening to some tab and then I pause it and want to listen to a song in Rhythmbox, it crashes and i have to close it through "force quit", and in the other way, if i'm listening to a song and then I pause it, when i want to hear the tab, a window pops out that says "MIDI System is unavailable".

Sound configurations in Tuxguitar 1.1:
MIDI Sequencer: TuxGuitar Sequencer.
MIDI Port: Java Sound Synthesizer. 
All the Plugins enabled too.

I want to know of there's a way to have both of them working simultaneously. 

Thanks =D.

---

### Post by marmotapl on 2009-12-03
Anyone?

I've tried TiMidity too... but if i change the MIDI Port the tab doesn't have any sound...

help plz!!! ='(

---

### Post by StuartN on 2009-12-03
> **marmotapl said:**
> I want to know of there's a way to have both of them working simultaneously.

(as an aside, one program should lock the resource and the other would simply be silent, not crash).

I think the answer is to start the Jack Audio Server before starting either application. I don't remember what setup is necessary for the applications, but it was not too painful.

---

