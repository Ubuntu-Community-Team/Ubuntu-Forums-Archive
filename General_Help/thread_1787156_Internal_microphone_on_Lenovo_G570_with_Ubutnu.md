---
title: "Internal microphone on Lenovo G570 with Ubutnu?"
date: 2011-06-20
forum: General Help
---

### Post by Marzata on 2011-06-20
The internal microphone doesn't work on brand new Lenovo G570 with Ubutnu 11.04. Any idea how to fix it? The external microphone works perfectly when connected. &#65279;Thank you!

---

### Post by Marzata on 2011-07-06
Any idea?

---

### Post by aruizcon on 2011-07-11
I have the same problem with my Lenovo G570.

---

### Post by aruizcon on 2011-07-16
I've solved it!.

You must edit /etc/modprobe.d/sound.conf

```
options snd-hda-intel model=asus
```I'm using Kubuntu 11.04, and I had "model=thinkpad" by default. Changing to "model=asus" and reboot alsa with:

```
sudo alsa force-reload
```Note: Sometimes, when I've tried  to reload service alsa, it failed because pulseaudio was working. Reboot and go.

You could test it with:
```
arecord -D hw:0,0 -vv -f cd ~/test.wav
```> **Marzata said:**
> The internal microphone doesn't work on brand new Lenovo G570 with Ubutnu 11.04. Any idea how to fix it? The external microphone works perfectly when connected. &#65279;Thank you!

---

### Post by Marzata on 2011-10-21
Thank you for your answer. I am running Xubuntu 11.10 and 
/etc/modprobe.d/sound.conf  
is empty. 
Any idea how to fix the issue above?

---

### Post by aruizcon on 2011-10-21
You must be sure that the module is loaded correctly:

```
$ lsmod | egrep snd_hda_intel
```If the module snd_hda_intel has been loaded, you could create the file /etc/modprobe.d/sound.conf  if it does not exist, or add the line if it is empty.


> **Marzata said:**
> Thank you for your answer. I am running Xubuntu 11.10 and 
/etc/modprobe.d/sound.conf  
is empty. 
Any idea how to fix the issue above?

---

### Post by Marzata on 2011-10-21
Thank you! The internal microphone works now. Is there a way to turn it up? Thank you again!

---

### Post by aruizcon on 2011-10-21
> **Marzata said:**
> Thank you! The internal microphone works now. Is there a way to turn it up? Thank you again!

You can change volume levels with:

```
$ alsamixer
```

---

### Post by Marzata on 2011-10-21
There in alsamixer I am not sure what should be the mic control. See the attached screenshot. Thank you!

---

### Post by aruizcon on 2011-10-22
Hi Marzata!

my internal mic control is "Analog Mic Boost". I can turn it up to 40dB. In your screenshot, it is on 30.

But my Chip is Conexant CX20590. Yours is "Intel CougarPoint HDMI". Is it the graphic card? On alsamixer, you can press F6 to select sound card.

---

### Post by TopOracle on 2012-01-29
Yes, this does work and even on Ubuntu 11.10. I've gotten a G770 (same specs as G570 but with 17" screen) to work. My sound.conf was empty but I entered the "options snd-hda-intel model=asus" and restarted the system, and the MIC works perfectly now.

> **aruizcon said:**
> I've solved it!.

You must edit /etc/modprobe.d/sound.conf

```
options snd-hda-intel model=asus
```I'm using Kubuntu 11.04, and I had "model=thinkpad" by default. Changing to "model=asus" and reboot alsa with:

```
sudo alsa force-reload
```Note: Sometimes, when I've tried  to reload service alsa, it failed because pulseaudio was working. Reboot and go.

You could test it with:
```
arecord -D hw:0,0 -vv -f cd ~/test.wav
```

---

### Post by Marzata on 2012-01-29
Lenovo G570 is a crap! The laptop box started to disintegrate. Avoid it!

---

### Post by eltomito on 2012-05-29
Thank you, aruizcon! 

I had the same problem and your solution worked. :guitar:
I just had to restart the system, because alsa didn't want to reload
the modules (saying "unload failed: these modules are still loaded...").

---

### Post by formateuPL on 2012-10-14
Sorry for offtopic, I have already the same problem on Ubuntu 12.04, but there file sound.conf doesnt exist, anyone know what to do with that?

---

### Post by aruizcon on 2012-10-14
> **formateuPL said:**
> Sorry for offtopic, I have already the same problem on Ubuntu 12.04, but there file sound.conf doesnt exist, anyone know what to do with that?

Do you try to create it?

---

### Post by formateuPL on 2012-10-14
Creating of file solved problem, thanks for help, sorry for spam:)

---

