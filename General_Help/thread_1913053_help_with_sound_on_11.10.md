---
title: "help with sound on 11.10"
date: 2012-01-21
forum: General Help
---

### Post by 50uth3rn on 2012-01-21
hi, i was trying to get the sound to go through the hdmi on my dell laptop. ive done it before but in the sound settings menu thing that i get from clicking on the sound icon at the top i clicked the wrong setting. the sound settings window then froze and eventually close. now i have a picture of a speaker and instead of ))) next to it its just a speaker with --- next to it. i cant control the volume with it and if i click on the settings box it doesnt list any input/output/hardware anywhere, its just blank. what can i do to get it back to normal? ive reinstalled pulseaudio incase it was something to do with that but that hasnt fixed it. the strange thing is if i log onto my laptop with a guest account everything is normal. my sound does work through but i cant control the volume or anything. can anyone help?
if i run pulse audio from a terminal i get this:

adam@tabitha:~$ pulseaudio
E: [pulseaudio] module-ladspa-sink.c: Master sink not found
E: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=1.1,2.1,3.2,1.8,0.0,0,0,0,0,0,0,0,0,0,0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialise daemon.

thanks in advance

---

