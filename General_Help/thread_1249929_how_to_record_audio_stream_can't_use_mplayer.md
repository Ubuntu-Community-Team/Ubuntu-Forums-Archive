---
title: "how to record audio stream? can't use mplayer"
date: 2009-08-25
forum: General Help
---

### Post by takayuki on 2009-08-25
Hi,

How can I record an audio stream without using mplayer -dumpstream?  The audio is on a password protected page and locked in a proprietary flash player.

Just need to record the output, but dunno how.  Been readin' but get bogged down in alsa, pulse, jack, oss, etc.

I'm using Ubuntu 9.04.

thanks for your help.

takayuki

---

### Post by takayuki on 2009-08-30
**How to record any audio output from any source**

this fix via: [http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/](http://carthick.wordpress.com/2007/11/26/linux-recording-soundcard-output-using-arecord/)


**Setup:**

1. click top right speaker icon > volume control > HDA Intel (Alsa mixer) > Options > Input Source > Front Mic (if Mix is available, use Mix, but my mobo ain't got it.  Main thing here is that there isn't anything plugged into the Front Mic port.)

2. start the audio (stream, or whatever) so you can hear it through your speakers or headphones.

**Record:**
*in the terminal:*

arecord -d 8500 -c 2 -f S16_LE -r 44100 -t wav -D copy foobar.wav

*notes: -d 8500 = record for 8500 seconds... set accordingly*

*if you don't have arecord:* sudo apt-get install arecord


**Encode the wav file to mp3 or ogg:**
*in the terminal:* 

lame -h foobar.wav 20090827jags.mp3

oggenc foobar.wav -o 20090827jags.ogg


*notes: only got output in left channel.  don't care though.  sound is ok.  Don't use 6 channel.  this worked for me.  hope it helps someone!*

regards,

takayuki

---

### Post by andrew.46 on 2009-09-12
Hi takayuki,

> **takayuki said:**
> 
```

lame -h foobar.wav 20090827jags.mp3
oggenc foobar.wav -o 20090827jags.ogg
```



Would you consider embellishing your audio conversion a little? For example:


```

lame **[COLOR="Red"]--alt-preset standard[/COLOR]** foobar.wav 20090827jags.mp3
oggenc **[COLOR="Red"]-q 6[/COLOR]** foobar.wav -o 20090827jags.ogg

```

Andrew

---

