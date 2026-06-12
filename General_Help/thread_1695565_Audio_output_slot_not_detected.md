---
title: "Audio output slot not detected?"
date: 2011-02-26
forum: General Help
---

### Post by Datweakfreak on 2011-02-26
The slots provided at the front of my CPU for headphone and Microphone output stopped working long back, so I've been using the two audio output slots at the back for sometime now, one for speakers and one for headphones. Both of them work fine in Windows, but only one of those slots is functional in Ubuntu. 

I'd be grateful if I can get help in getting this fixed.

Thanks in advance :)

---

### Post by DanneStrat on 2011-02-26
> **Datweakfreak said:**
> The slots provided at the front of my CPU for headphone and Microphone output stopped working long back, so I've been using the two audio output slots at the back for sometime now, one for speakers and one for headphones. Both of them work fine in Windows, but only one of those slots is functional in Ubuntu. 

I'd be grateful if I can get help in getting this fixed.

Thanks in advance :)

I will see if I can help you.

First I need some info about your sound card

so please do the following:

Open a terminal and do:

```
sudo aplay -l
```

Post the output.

---

### Post by Datweakfreak on 2011-02-26
> **DanneStrat said:**
> I will see if I can help you.

First I need some info about your sound card

so please do the following:

Open a terminal and do:

```
sudo aplay -l
```Post the output.

Thanks!

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by DanneStrat on 2011-02-26
We will begin by checking that

your pcm-, master- and headphone

channels are unmuted.

Do this.

Open a terminal and launch alsamixer:

```
alsamixer
```If you find out that any the channels

i mentioned above is muted (showing "MM")

unmute it by pressing the "m" key

and increase the volume with the "up" arrow key.

Check if you get sound.


If not you can try the following.

In a terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Carefully look for the line "options snd-hda-intel model=xxxx[B]"

[/B]Note down what the line says after the "="
so you can put it back if this doesn't work.
Now modify the line so it looks like this[B]:

[/B]```
options snd-hda-intel model=auto
```Save the file (file >save) and exit.

Now reboot your computer and check if you have sound.

---

### Post by Datweakfreak on 2011-02-26
Here is a screenshot of my alsamixer. 

[http://i55.tinypic.com/96avqx.png](http://i55.tinypic.com/96avqx.png)

The Headphone channel is not muted, but I'm not able to increase the volume. I've also tried altering the conf file like you said, but it doesn't work.

---

### Post by DanneStrat on 2011-02-26
> **Datweakfreak said:**
> Here is a screenshot of my alsamixer. 

[http://i55.tinypic.com/96avqx.png](http://i55.tinypic.com/96avqx.png)

The Headphone channel is not muted, but I'm not able to increase the volume. I've also tried altering the conf file like you said, but it doesn't work.

Can you give some more info about your computer?

Make and model etc.

---

### Post by Frogs Hair on 2011-02-26
Here is a related thread.[http://ubuntuforums.org/showthread.php?t=1624557](http://ubuntuforums.org/showthread.php?t=1624557)

---

