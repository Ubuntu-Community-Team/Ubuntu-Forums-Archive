---
title: "Sound plays through both headphones and speakers simultaneously"
date: 2010-05-16
forum: General Help
---

### Post by Snomi94 on 2010-05-16
I'm using a new acer laptop 7736G with x64 ubuntu 10.04
Sound plays through both headphones and speakers when attached. 
When I use alsamixer and mute either the speaker or headphones, both of them mute.
When I alter the volume of the 'headphone' column, nothing happens.
If you need any more detail about my sound card etc I can go find it...

Thanks in advance for any help

---

### Post by Snomi94 on 2010-05-25
bump :(

---

### Post by grege on 2010-05-25
Whenever I have issues I install Gnome-alsamixer through Synaptic as it has lots of options. When running select Edit -> Sound card properties" and make sure all the channels are visible.

Next step would be to Google "ALSA Acer 7736G " and see what pops up.

Only general ideas.

---

### Post by grege on 2010-05-27
Google does not help, except that this bug has been around for a while.

Acer never mention the audio chipset in their specs, only calling it Dolby this and Dolby that, but never what it is.

The Windows driver is a Realtek, so that is a start.

So.....

run dmesg in a terminal and look through the output for a line starting with hda_codec and see what chip is identified, then start searching for answers with that information.

---

### Post by Snomi94 on 2010-05-27
hda_codec: ALC888: BIOS auto-probing

---

### Post by grege on 2010-05-27
Try editing (as sudo) /etc/modprobe.d/sound and rebooting

Add at the end, or modify an existing line if there is one.

options snd-hda-intel model=auto

or
options snd-hda-intel model=acer
or
options snd-hda-intel model=acer-aspire
or
options snd-hda-intel model=3stack

OR - from the alsa documentation

3stack (3-jack in back and a headphone out)
3stack-digout (3-jack in back, a HP out and a SPDIF out)
5stack (5-jack in back, 2-jack in front)
5stack-digout (5-jack in back, 2-jack in front, a SPDIF out)
6stack (6-jack in back, 2-jack in front)
6stack-digout (6-jack with a SPDIF out)

BUT ONLY one at a time

Lucid uses Alsa 1.0.22

For an ALC888 there are many options for various machines but these look like the most likely.

---

### Post by mlhudson on 2010-07-10
Did you get this sorted out? I'm having similar issues with an Acer Aspire 7736z. Would love to know the cure...

---

### Post by m3n7al.piracy on 2010-11-02
I have an HP tx2000 tablet, but I don't think it matters what kind of computer you have. In Ubuntu 10.04 if you left click on the speaker in the top panel and go to preferences, then go to the output tab, on the connector type select analog output, and voila. Downside is you have to manually change it if you want sound coming out of the speakers instead. Definitely a needed change for a later release, (hint hint) ;)

---

