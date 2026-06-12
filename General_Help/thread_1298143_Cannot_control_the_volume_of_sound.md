---
title: "Cannot control the volume of sound?"
date: 2009-10-22
forum: General Help
---

### Post by mac666 on 2009-10-22
Hey
I use my graphiccard with DVI>HDMI output to get sound and video in same cable. 
But i cannot do anything to control it..!

Lower volume in volumecontrol doesnt do it. If i mute the sound it works to mute it , but i cannot control either channels of it. 

Image: [http://img32.imageshack.us/img32/8254/printscreenrg.jpg](http://img32.imageshack.us/img32/8254/printscreenrg.jpg)

I cannot change the standard device, i only have HDA Intel (Alsa Mixer)

If i open alsamixer in terminal, i still cannot lower or raise to volume or controll it in any way..?!

Edit: If i do a sound test **speaker-test -Dplug:surround50 -c4 -l1 -twav** i dont hear anything, but if i play music et c... i hear ?!
Edit #2: Now with the sound test that is mentioned above, i get msg: **Fel vid öppning av uppspelningsenhet: -16, Enhet eller resurs upptagen** aka **Error when opening the playback device: -16, Device or resource busy.**
This is Really bugging me!

---

### Post by mac666 on 2009-10-23
Come on! Someone must know something? :(

---

### Post by Lantesh on 2009-10-27
Here are my mixer settings in gnome-alsamixer.  Take note of the IEC958 setting.  I have a physical connection running from a S/PDIF header pin on my mother board to the input on the side of my Nvidia 9600 GT.  That along with these mixer settings give me pass through audio via a DVI to HDMI adapter.  On occasion if my audio doesn't work I have to check the IEC958 mute check box, and then uncheck it, and that resets it.

---

### Post by mac666 on 2009-10-28
i seem to have the same settings as you... well, i guess i allways could use the reciver to raise or lower volume...

Do you know why my audio may only be used by one instance at the time?

If i open Totem (The movieplayer) and play something, and then open for example VLC, and play something, the sound from totem disappears?

Thanks!

---

