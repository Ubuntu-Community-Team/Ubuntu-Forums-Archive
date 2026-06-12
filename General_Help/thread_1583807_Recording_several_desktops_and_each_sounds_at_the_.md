---
title: "Recording several desktops and each sounds at the same time"
date: 2010-09-28
forum: General Help
---

### Post by pabloadr on 2010-09-28
Hi everyone.

Im trying to develop a system that records different desktops at the same time. I have developed a audio-videochat system and I want to be able to record what happens in every room, so my starting idea was:

1) Open a graphic terminal for each room. I have succeeded using vncserver :NumberDisplay. 
2) In each terminal, run firefox at each URL. I succeeded too because firefox lets me specify in wich NumberDisplay I want it to be open
3) In each terminal, run recordmydesktop to record. It allows too to specify the NumberDisplay.

My problem now is that it seems that the sound card is "shared", so the sounds recorded in the display 1 includes the sound generated in all others firefox windows. I havnt found an analogy for the sound as the display is for the graphics.

I have thought some ideas but I havnt been able to materialize anyone. 
Im tried to create virtual sound cards and specify one for each vncserver, I tried to redirect the sound of each firefox window to one "channel" (read firefox delegates the sound so that might not be an option), I read many things about pulseaudio, jack and several stuff that I just havnt been able to work.

Any idea, guide, tutorial, opinion or comment is appreciated.

Thanks for your help.

Regards

---

### Post by pabloadr on 2010-09-29
Noone?

---

### Post by pabloadr on 2010-10-01
Any kind of help is welcome.

Thanks :)

---

