---
title: "How do rip in 128 bitrate ogg vorbis with Sound Juicer?"
date: 2006-06-03
forum: General Help
---

### Post by mostwanted on 2006-06-03
I'm not really into  encoding profiles and SJ only comes with one type of Ogg encoding - how do I add a 128bit ogg profile to Sound Juicer (and don't recommend me other programs as a solution, please).

Thank you for your time!

---

### Post by slimdog360 on 2006-06-03
use another program *sorry I couldnt help myslef*

---

### Post by mostwanted on 2006-06-03
*bump*

Someone else has got to know this...

---

### Post by whatever on 2006-06-03
why the f*** do you want to use ogg vorbis with constant bitrate? ogg vorbis was designed for vbr...
a quality setting of 4 should result in an average bitrate of 128kbit for most content.

---

### Post by mostwanted on 2006-06-03
[QUOTE=whatever]why the f*** do you want to use ogg vorbis with constant bitrate? ogg vorbis was designed for vbr...
a quality setting of 4 should result in an average bitrate of 128kbit for most content.[/QUOTE]

Thank you!

No need to swear. I don't mind that my files have a variable bitrate, but I need to have them a bit smaller than they are by default in Ubuntu.

---

### Post by meng on 2006-06-03
If you go to preferences and edit profiles, (CD Quality Lossy), you probably have:

audio/x-raw-int,rate=44100,channels=2 ! vorbisence name=enc quality=0.5 ! oggmux

You'll need to add
bitrate=128

If you want CBR, add
vbr=0

(I'm not sure if you need to keep the quality=0.5 bit or get rid of it).

---

### Post by mostwanted on 2006-06-04
I don't get the quality thing.

If I set the quality bit to the default 0.5 song no. 1 is 6 mb in size, if I set it to 4 it becomes 4.2, but if set to 1 it's 18.3 mb. This doesn't make sense to me, can someone explain?

(haven't used meng's advice yet, not sure if I want a constant bitrate...)

---

### Post by dexterchief on 2008-06-12
I have been looking to change the bitrate in sound juicer as well, only up to 192 instead of down to 128. After a little playing around with editing the output format profiles this is what I found:

(this is all in the gstreamer pipleline setting)
quality=0.4 gives 128 kbps
quality=0.5 gives 160 kbps
quality=0.6 gives 192 kbps

Adding bitrate=192 did not seem to have any effect.

I think the only reason to use constant bitrate is when you want to use the files for streaming/internet radio type stuff...

---

