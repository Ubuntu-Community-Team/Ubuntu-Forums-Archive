---
title: "PLease help, mic not working. I have tried everything, no one could help thus far."
date: 2009-11-14
forum: General Help
---

### Post by Xtozze on 2009-11-14
First of all i am new to ubuntu, and since last night have loved it and hated it. I have tried everything i possibly could. to fix the issue. I also visited #ubuntu for the entire day and no one there could really help either. But thank you for those who tried.

OK. The issues i weird. Its as if it didn't recognize a microphone at all. Yet i can hear sound perfectly fine. At first people thought my things we're muted so i checked. Then it was more complex like drivers so we looked at all of that... nothing seems unusual. 

Regardless ill be here the whole day if i explain yesterday. JUst please ask away any questions or give any commands for anything i can try to make this mic work. Ill be here until it hopefully gets fixed.

I really like ubuntu but if i can't fix the mic i can't keep it. I hope someone there can help me.

thank you in advance, Clay.

---

### Post by RedSingularity on 2009-11-14
Have you installed pulseaudio?

---

### Post by Xtozze on 2009-11-14
bump, i really need this to work.

I have just tried every system all of them act as if no microphone was there btw i am using a laptop's mic and a plugged in mic and they both work on windows

---

### Post by Xtozze on 2009-11-14
> **RedSingularity said:**
> Have you installed pulseaudio?


Installed pulse audio just now but i don't see how i can use it to fix this.. I see no relevant options.

---

### Post by RedSingularity on 2009-11-14
It may be installed by default.  Install the "padevchooser".  Then go to sound and video and choose pulseaudio device chooser.  That will start a deamon which you will see in the notification area / system tray.  Click that and mess with the options.  This is how i got a headset working that i had really given up on.

---

### Post by toammann on 2009-11-14
Have you searched for you chipset and stuff... some hardware does have issues, and if so you will probably find information somewhere on the net. I just had to install a newer version of alsa, because the one packaged with ubuntu didn't recognize my eeepc's mic.

---

