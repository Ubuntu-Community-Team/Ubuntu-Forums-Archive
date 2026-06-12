---
title: "Audio line input not working"
date: 2012-06-23
forum: General Help
---

### Post by cbraxton on 2012-06-23
It seems ever since pulseaudio debuted whenever updating to a new version of Ubuntu it's always a problem to get the audio working properly. This time is no exception, I've just installed Xubuntu 12.04 64-bit in place of Ubuntu 10.04. Audio hardware is a Sound Blaster Audigy card. 

Simple audio playback is generally OK, though sound from VLC had a lot of static, fixed this by directly selecting the Sound Blaster for output instead of the pulseaudio server in VLC's audio settings. 

The biggest problem is that the line input is not working. On 10.04 if an analog audio source was fed in it would play through the computer speakers and would be available for recording in Audacity or other programs. (This did not work by default, it took a a fair amount of mucking around at the time though I don't recall details.)

On Xubuntu 12.04 under "Sound Settings" the only input device shown as available is the microphone input. The microphone does work for recording, but does not output through the speakers. It seems impossible to select the audio card's line input as it is simply not listed in the dropdown list under "Input Devices."

So... two questions:

1. How can I get the line input working?
2. How do I get the speakers to monitor what comes in on the input?

Thanks in advance to anyone who can supply the appropriate mystical incantations!

-----

UPDATE:

I found that by using the xfce4-mixer program it was possible to enable the line input on the audio card, and by turning up the "Analog Mix" slider monitoring to the speakers is enabled. (Sound Settings still shows only the microphone available!)

I remember now this is basically what I had to do on 10.04 to get this working, but being a couple of years I didn't remember that until posting this message...

---

### Post by schneil on 2012-08-13
I had exactly the same problem.
I had to use the command line alsamixer to turn up analogue mix.  Works fine now.

I can't alter the input volume in audacity though, I have to use alsamixer

---

