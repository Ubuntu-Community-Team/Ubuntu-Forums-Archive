---
title: "No sound in Flash"
date: 2010-10-29
forum: General Help
---

### Post by kenpuu on 2010-10-29
Hello!! Please help me!!

I have a X-Fi Xtreme Audio PCI-E CA0110-IBG. Until this week(or last maybe) it didn't work, but I tried with Alsa Script([http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)), it sounds!! I'm very happy :P

Anyway, Flash has no sound. I've created ~/.asoundrc, because I've seen in many forums that's the solutions, but I don't unterstand how it works. My outputs:

aplay -l

```

tarjeta 0: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Creative [HDA Creative], dispositivo 0: CA0110 Analog [CA0110 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Creative [HDA Creative], dispositivo 1: CA0110 Digital [CA0110 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

cat /proc/asound/cards
```

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeafc000 irq 29
 1 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xfe9fc000 irq 17

```

I've tried some modifications to .asoundrc. 
```


defaults.pcm.card 1


```
-------------------
```


defaults.ctl.card 1


```
-------------------
```


defaults.pcm.card 1
defaults.ctl.card 1


```

With those three Flash sounds but the rest don't.
-------------------
```

pcm.!default {
    type hw
    card 1
    device 0
}

```

With this it is like if the file doesnt exists.

I want to select the X-fI output. Can anyone explain how .asoundrc or alsa.conf works? I've sarched in many forums, but I don't get. Thanks in advance. And sorry for my English!! :P

-----------------------------------
ESPAÑOL
-----------------------------------
Hola a todos. Necesito ayuda!!! :D

Tengo una X-Fi Xtreme Audio PCI-E, la cual hasta hace poco no funcionaba, pero ya con el último snapshot de alsa-driver sí. El caso es que va perfecta, excepto que no hay sonido en flash.

Tocando el .asoundrc he conseguido que haya, pero entonces el resto de programas no van. Me estoy volviendo un poco loco porque no entiendo bien como funciona.

Mis salidas de aplay -l y cat /proc/asound/cards son respectivamente:

aplay -l
```

tarjeta 0: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Creative [HDA Creative], dispositivo 0: CA0110 Analog [CA0110 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: Creative [HDA Creative], dispositivo 1: CA0110 Digital [CA0110 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

cat /proc/asound/cards
```

 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeafc000 irq 29
 1 [Creative       ]: HDA-Intel - HDA Creative
                      HDA Creative at 0xfe9fc000 irq 17

```

He probado a hacer estas modificaciones al .asoundrc:
```


defaults.pcm.card 1


```
-------------------
```


defaults.ctl.card 1


```
-------------------
```


defaults.pcm.card 1
defaults.ctl.card 1


```

Con esas tres me suena Flash pero para el resto pone salida boba.
-------------------
```

pcm.!default {
    type hw
    card 1
    device 0
}

```
Para esta suena todo excepto Flash.

Quiero seleccionar la salida analógica de la X-Fi. Ya de paso, ¿puede alguien explicar cómo funciona el archivo? Porque he mirado mucho en foros y no lo acabo de entender. Tengo instalado Lucid. Gracias de antemano.

---

### Post by kenpuu on 2010-11-05
up

---

### Post by kenpuu on 2010-11-05
At the end I had to install this:
[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

It solves the youtube problem, but flash is still whitout sound.

---

### Post by lkjoel on 2010-11-05
I had the same problem, until I used OSS.
OSS fixed it all.
Try Fix your sound! in my signature, and then use Post-Fix your sound! in my signature.

---

### Post by kenpuu on 2010-11-07
> **lkjoel said:**
> I had the same problem, until I used OSS.
OSS fixed it all.
Try Fix your sound! in my signature, and then use Post-Fix your sound! in my signature.

I had OSS, but it only let me use two channels, and i wanted to have 5.1. Also, ubuntu is is more compatible with alsa i think. However, I dno't know what is Post-fix. Could you explain me that?

---

### Post by lkjoel on 2010-11-07
> **kenpuu said:**
> I had OSS, but it only let me use two channels, and i wanted to have 5.1. Also, ubuntu is is more compatible with alsa i think. However, I dno't know what is Post-fix. Could you explain me that?
If you have OSS 4.2 installed (the current version), the Post-Fix will make the sound work anytime you don't have it working.

---

### Post by efflandt on 2010-11-07
What shows up in Sound Preferences in gnome for Hardware and Output?

This may or may not work, but you might try creating /etc/modprobe.d/sound.conf with:

```
options snd-hda-intel enable_msi=0 probe_mask=1,2
```and/or create /etc/asound.conf with:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```See if the sound tests work under Sound Preferences > Hardware tab, and if they do, this should allow you to select Output device with Sound Preferences.  Without that flash tends to use whatever your default alsa device is (in alsamixer) instead of what is selected with pulse audio (which in your case appears to be HDMI).  That allows me to use Sound Preferences to select output for everything including flash, except my built-in sound shows up as card 0 and (nvidia) HDMI as card 1.  Note that you need to use sudo to edit system files as root, and if you have your own ~/.asoundrc, that may interfere with /etc/asound.conf.

I cannot say if that will work with ATI HDMI and your sound card, but since it seems to use snd-hda-intel it is worth a try.  In my case I can select either analog stereo or HDMI stereo using Sound Preferences.  But you may need to set the Hardware tab there to something other than Analog Stereo Duplex for your sound card.

---

### Post by kenpuu on 2010-11-08
Thank you! You're a genius!! :P

I still don't understad how sound.conf works. Thanks again!

---

