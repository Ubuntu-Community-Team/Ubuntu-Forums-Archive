---
title: "Interface Problems"
date: 2006-01-23
forum: General Help
---

### Post by Alchazz on 2006-01-23
I am new to Ubuntu. I downloaded 5.10. It installed easily and seems to be very user friendly....BUT

So:confused:  far, I have not been able to get anthing to print even though the system finds my printer, IDs it and the little printer icon pops up. But nothing happens at the printer. Yes I downloaded the proper driver and installed it. Still "No Joy."

Also, I thought I would try out the CD player. Arrgh! It "plays" as shown on the progress bar. It IDs the songs, etc. But, no sound. Oh, and the sound system works as it works just fine under Winders.

I think I'm lucky then that my ethernet connection works. What is this with problems with the interfaces?

---

### Post by Alchazz on 2006-01-23
[QUOTE=jazzgossen]Have you tried "Print test page" in the printers dialog? Do you get any status or error messages when doing that, such as "port busy" or something else?

Do you have multiple audio outputs? I've had some problems with optical SPDIF output from my soundcard. Try changing to the stereo jack instead of SPDIF, or vice versa, if possible.[/QUOTE]

"Print test page" behaves the same way. There are no error messages.

I have only one simple output on the sound card.

My computer has installed in it replaceable HD modules. I can change operating systems by just replacing a module. When I use the windows module, all works as advertised. It even works when I use the RH 9 module. So it's not the hardware that's hinky.

---

### Post by jazzgossen on 2006-01-23
Have you tried "Print test page" in the printers dialog? Do you get any status or error messages when doing that, such as "port busy" or something else?

Do you have multiple audio outputs? I've had some problems with optical SPDIF output from my soundcard. Try changing to the stereo jack instead of SPDIF, or vice versa, if possible.

---

### Post by Alchazz on 2006-01-24
[QUOTE=jazzgossen]Have you tried "Print test page" in the printers dialog? Do you get any status or error messages when doing that, such as "port busy" or something else?

Do you have multiple audio outputs? I've had some problems with optical SPDIF output from my soundcard. Try changing to the stereo jack instead of SPDIF, or vice versa, if possible.[/QUOTE]
OK,  solved the sound problem. What an ordeal. I thought that doing the audio preferences would be enough. No way, Jose! I finally found something called Multimedia System Selector. I played with the various audio options, no guidance, of course, and finally something called ALSA in the Sink and Source locations did the trick. This was a little obtuse for me.

I still have to fight the printer problem. What devious path have I not followed yet?

---

