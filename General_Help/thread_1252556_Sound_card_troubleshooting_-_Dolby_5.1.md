---
title: "Sound card troubleshooting - Dolby 5.1"
date: 2009-08-29
forum: General Help
---

### Post by plasmamist on 2009-08-29
Howdy,
     I just installed Jaunty (I myself am very new to Ubuntu) and am having some sound card difficulties.
I have an on board device (Nvidia) that works, but my Audigy 2 device (currently setup for Dolby 5.1) produces no sound.
Unfortunately, I am a Windows admin, and I don't know where to start... :)

I would like to know how to use my 2nd sound card, preferably, supporting Dolby Digital.

Thanks,

---

### Post by khelben1979 on 2009-08-29
I have no experience on setting up the sound system graphically, but these 2 methods work:

```
sudo alsaconf
```
to choose your soundcard. If the tool isn't installed you can search for it using the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager"). It's part of [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture").

```
sudo alsamixer
``` or ```
sudo alsamixergui
``` to adjust your volume settings afterwards including set a tick at the Audigy Analog/Digital Output to be able to hear anything from it.

I have a [Sound Blaster Audigy 2 ZS]("http://en.wikipedia.org/wiki/Sound_Blaster_Audigy#Sound_Blaster_Audigy_2_ZS") soundcard which works perfectly with Linux.

---

### Post by plasmamist on 2009-08-29
I ran the 'alsamixer' command and found a muted "Audigy Analog/Digital Output Jack".  When I mute/unmute it, I hear a loud 'bump' come from my woofer.  But, unfortunately, no actual sound from any applications.

Anything else?

---

### Post by jocko on 2009-08-29
> **plasmamist said:**
> Howdy,
     I just installed Jaunty (I myself am very new to Ubuntu) and am having some sound card difficulties.
I have an on board device (Nvidia) that works, but my Audigy 2 device (currently setup for Dolby 5.1) produces no sound.
Unfortunately, I am a Windows admin, and I don't know where to start... :)

I would like to know how to use my 2nd sound card, preferably, supporting Dolby Digital.

Thanks,
If you mean you want to use the dolby digital live functionality (hardware on-the-fly re-encoding of all sound to dolby digital) of the sound card, then give it up. It's not possible with the linux drivers. Dolby Digital is proprietary technology, so the sound card manufacturers can not give out the necessary information to make drivers that can activate that part of the sound card.

But if you mean you want spdif pass through of already encoded dolby digital (i.e sound in a DVD or video file), then it shouldn't be too difficult to accomplish.

Or do you simply mean you want to use the digital output (spdif) as output for all sound? This does not result in dolby digital, or any other surround sound, but it simply sends the sound as a digital stereo signal to your amplifier. But this should not be very hard to do either.

---

### Post by plasmamist on 2009-08-29
... Rats...

The point of using the other card was for the Dolby piece, and I don't really have much stuff that is pre-encoded, ready for pass through.

Thanks for the info though - I though there would have been Linux drivers to accommodate.

So, as a close to this thread, Dolby re-encoding is reserved for Windows only?

Thanks again!

---

### Post by jocko on 2009-08-29
> **plasmamist said:**
> ... Rats...

The point of using the other card was for the Dolby piece, and I don't really have much stuff that is pre-encoded, ready for pass through.

Thanks for the info though - I though there would have been Linux drivers to accommodate.

So, as a close to this thread, Dolby re-encoding is reserved for Windows only?

Thanks again!
As far as I know, yes. Nvidia had a closed source OSS linux driver for their soundstorm chipset (on some high-end nforce2 motherboards) that could activate the dolby digital encoder, but that driver (as well as the sound chipset itself) was discontinued several years ago... So unless Creative (or some other sound card manufacturer) decides to make a full-featured closed source linux driver (very unlikely as long as linux has such a low market share as it does) or Dolby labs decides to drop the DD patent and allow release of the specs (this will of course never happen), there will probably never again be any linux driver with dolby digital live capability...

---

### Post by grepster on 2010-01-31
This is actually possible using alsa plugins. See [http://www.johannes-bauer.com/dolby/](http://www.johannes-bauer.com/dolby/)  I tried it and it worked, but am not using it as I can not see the use of it as my music is already sent digitally through spdif and encoding it in another lossy format does not make sense to me.  And my amplifier can already simulate surround by routing signals to various speakers.  Maybe someone can explain what the benefits would be.

---

