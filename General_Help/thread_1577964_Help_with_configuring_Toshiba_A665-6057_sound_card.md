---
title: "Help with configuring Toshiba A665-6057 sound card(s)?"
date: 2010-09-19
forum: General Help
---

### Post by ngrieb on 2010-09-19
Hey all, 
Just got my wife a new Toshiba A665-6057. So far no large problems or complaints running Ubuntu 10.04 x64, but this one:

I can get sound out of the speakers just fine, but the headphones and mic (neither jack nor the one inlaid in the laptop) don't seem to work. I have read a few posts about getting the mic working again, but the model was slightly different. Still attempted them with no success. The thing is I think this computer might have two integrated sound cards or at least a realtek and nVidia card shows up in my gnome alsa-mixer gui. I can't find any mention of these things in the lshw output though.

Can anyone help me configure my sound card(s)? 

I'm not sure what's going on here...cause this has never been an issue for me before. 
Thanks.

---

### Post by ngrieb on 2010-09-20
Just an update...I trued the dvi cable out this afternoon, and I cannot get any sound out of it either. (All issues which are not apparent in Win7...so they are definitely sound card software/driver related most likely something with pulseaudio). Also when I peek into /dev/ I see two mixers: mixer and mixer1...is this where the issue is coming from? I show the usual /dev/dsp and /dev/audio other than that. I have really not poked too much into sound devices in Linux so any troubleshooting help would be awesome. 

If I need to post any other info hw related or sound output info please let me know what I need to do to help narrow down the issue. Thanks.

---

### Post by ngrieb on 2010-09-20
Ok, well I really need help now cause after the HDMI attempt there was no sound at all through anything. I tried futzing a bit with the sound settings...and now I can no longer see my sound card in the gnome sound settings manager. I have no clue how to get it back. =-(

After even more researching...it seems that the audio codec needed by ALSA has a bug. I attempted to get the new and unsupported ALSA codecs through an update script that some nice person put together. Long story short...I now have mic, HDMI, and headphone support...but now I cannot access the speakers...it recognizes them and has a channel for them...but the sound comes out of the headphone jack even if everything in the ALSA-mixer GUI and sound settings show speakers. Can anyone help with this problem?

something I'm missing in /etc/modprobe.d/alsa-sound.cfg maybe?

---

