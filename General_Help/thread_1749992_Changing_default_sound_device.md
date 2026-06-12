---
title: "Changing default sound device"
date: 2011-05-05
forum: General Help
---

### Post by Fanas on 2011-05-05
I have headphones connected via usb and every time I restart computer or disconnect them, my sound output is switched to laptop speakers. Is there a way to make so that every time the headphones are detected, they would be used automatically?

---

### Post by sg1efc on 2011-05-05
Not sure if this will help you, but I added:   pavucontrol
by using Synaptic Package Manager.  It gives me more settings to adjust than the regular Gnome Alsa Mixer program that comes with Ubuntu and works well for me to change audio output between my internal speaker, headphones, etc., for various running programs.

Be advised that that if you want to change an output device for some programs, you may have to experiment a bit, Example:

I use Pidgin as my instant messaging program. Wanted my audio alerts to be heard through my external speakers instead of through my headphones. However the Pidgin audio alert beep was too short for it to display long enough in Pulse Audio Volume Control (pavucontrol) for me to change that setting in time before it disappeared. So I changed the default Pidgin alert notification sound to the first 15 seconds of an Iron Maiden song (LoL) and that gave me a long enough time to see and change the Pulse Audio Volume Control (pavucontrol) from headphones to external speakers output.  :)

In Pulse Audio Volume Control (pavucontrol), there are icons to mute and unmute the programs you see in there. A little difficult to figure out whether or not Mute is on or off.

Also, it is possible that after using Pulse Audio Volume Control (pavucontrol), you might also have to go into the regular Gnome Alsa Mixer program that comes with Ubuntu and make adjustments in there.

One last thing is that there are quite a bit of various settings you can adjust in Pulse Audio Volume Control (pavucontrol), so be careful what you change in there.

---

