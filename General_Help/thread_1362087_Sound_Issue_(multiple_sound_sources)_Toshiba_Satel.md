---
title: "Sound Issue (multiple sound sources) Toshiba Satellite A100 please help!"
date: 2009-12-22
forum: General Help
---

### Post by stevan2002 on 2009-12-22
I can't use sound on multiple sound sources. It has been broken for a while but use to work back in kde3.5 for me. I think it is the alsa drivers.

If I am listening to music on amarok and try to watch a flash video on youtube the sound wont work on youtube. 

I have to close anything with sound open then I have to run 

sudo /etc/init.d/alsasound restart 

which fails the first time with this error message:

Shutting down sound driver: ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_hda_codec
ERROR: Module snd_pcm is in use by snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
done
ALSA driver is already running.

Then I run the same command again and get:

Shutting down sound driver: ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_hda_codec
ERROR: Module snd_pcm is in use by snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
done
ALSA driver is already running.

After this I can start flash, and listen to that, but then to listen to music I have to close my browser and music player and run the commands again. 

PLEASE HELP :D

---

### Post by reisewolf on 2009-12-30
Hi,

 exactly same problem here, got a workaround from somewhere with the following line in terminal:

sudo alsa force-reload

But I would be happy for a real fix of this issue.

Anyways have a good New Year everybody....

---

### Post by stevan2002 on 2010-01-09
sudo alsa force-reload seems to work but it would be very nice to be able to have sound coming from two sources at once. Are there any other solutions that anyone knows about?

---

