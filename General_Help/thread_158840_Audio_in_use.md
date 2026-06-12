---
title: "Audio in use?"
date: 2006-04-11
forum: General Help
---

### Post by fmpuk on 2006-04-11
I'm sure this can't be normal. Basically, if I have one program playing audio (say, Amarok) nothing else can play audio. For example no sound plays in flash movies if Amarok is playing and vice versa. Surely this is a fixable issue? Hopefully it isn't one of those 'Linux things'..

---

### Post by thunderduck3141 on 2006-04-11
yes, totally fixable (i think)
u probably have it set so that whatever sound is playing has high/realtime/root priority, this is causing ur system to play only that file untill it is done
try fiddling w/ ur sound system, or even try switching to OOS(or Alsa if ur using OSS)
hope that helps

---

### Post by fmpuk on 2006-04-12
Do you know how I would go about checking all the above? I'm not sure how to switch from one system to another etc. Thanks!

---

### Post by thunderduck3141 on 2006-04-12
what are u using, gnome or kde
kde is a pain when it comes to sound (at least for me) if ur using kde try using gnome
let me know what u r using though

---

### Post by DOtSlaSHuCantCME on 2006-04-12
A combination of the above solved and  taught me a lot about the sound setups,and how to get multiple sounds.

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=multiple+sounds)

[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=ALSA+mixing](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=ALSA+mixing)



===========================================
Heres some stuff i saved just in case i needed one or the other , this a asound.conf ,if u want fullduplex.   (bellow)
============================================

1.pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:0"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "card0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is espected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                0
}




============================================
Oh, since you have OSS through ALSA enabled, add this to the instructions to get sound in Firefox:

Edit /etc/mozilla-firefox/mozilla-firefoxrc change FIREFOX_DSP to "AOSS"

I've also noticed that if you're using RealPlayer, there's crackling in sounds unless you set buffer_size to 8192
==============================================

---

