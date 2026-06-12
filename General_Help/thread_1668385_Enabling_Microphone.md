---
title: "Enabling Microphone"
date: 2011-01-16
forum: General Help
---

### Post by cancer10 on 2011-01-16
Hi

I have installed ubuntu 10.04 on my lappy but the microphone does not seem to work. I tried recording my voice in the sound recorder but it does not. May be I need to turn it ON from somewhere?

Pls help

---

### Post by cancer10 on 2011-01-17
Anyone?

---

### Post by ptptaylor on 2011-01-17
In the top right panel, there is a speaker icon. Left click on that and go to sound preferences. Then go to input - is it unmuted and responding to input. Also check you are using the correct input as described in that panel.
Also check hardware and that you are using the correct hardware if you have multiple installed.

---

### Post by cancer10 on 2011-01-17
> **ptptaylor said:**
> In the top right panel, there is a speaker icon. Left click on that and go to sound preferences. Then go to input - is it unmuted and responding to input. Also check you are using the correct input as described in that panel.
Also check hardware and that you are using the correct hardware if you have multiple installed.



Attached is what i see...

---

### Post by ptptaylor on 2011-01-18
What system are you using? Is it an external sound card?

---

### Post by cancer10 on 2011-01-18
> **ptptaylor said:**
> What system are you using? Is it an external sound card?

No its a laptop with inbuilt sound card.

Configuration : [http://ubuntuforums.org/attachment.php?attachmentid=179969&d=1294039540](http://ubuntuforums.org/attachment.php?attachmentid=179969&d=1294039540)

---

### Post by matt-fender on 2011-01-18
run this in a terminal

```
alsamixer
```

press F5

Make sure mic capture etc is turned up

Press F6, make sure your sound card is definitely selected

---

### Post by cancer10 on 2011-01-26
> **matt-fender said:**
> run this in a terminal

```
alsamixer
```

press F5

Make sure mic capture etc is turned up

Press F6, make sure your sound card is definitely selected


Ok attached is the screenshot of alsamixer.

---

### Post by 0N3 on 2011-01-26
Can you post a pic of the hardware tab like the pic above where you posted the input tab

---

### Post by cancer10 on 2011-01-26
> **0N3 said:**
> Can you post a pic of the hardware tab like the pic above where you posted the input tab

There u go...

---

### Post by 0N3 on 2011-01-26
The Hardware Tab under sound preferences not alsamixer sorry for my confusion.

---

### Post by cancer10 on 2011-01-26
attachec

---

### Post by 0N3 on 2011-01-26
You have the correct settings im baffled as to why its not working.
So many people have it set to Analog Stereo Output and this listens to your speakers as such and doesnt pick your voice up when talking ideal for playing music via your mic in a chatroom ect.... But you have the correct settings.

---

### Post by 0N3 on 2011-01-26
Can you try 

sudo apt-get install gnome-alsamixer 

And post a screenshot of it thanks.

Its not the same as alsamixer.

---

### Post by cancer10 on 2011-01-26
Could this be a bug in ubuntu 10.04?

---

### Post by 0N3 on 2011-01-26
Try install gnome-alsamixer then run it and post your screenshot

sudo apt-get install gnome-alsamixer

I have a feeling somethings muted somewhere

---

### Post by cancer10 on 2011-01-26
Pfa

---

### Post by 0N3 on 2011-01-26
Im more confused now I cant see anything wrong in your settings :(
It should be recording

---

### Post by badnaam on 2011-01-26
I am seeing the exact same problem. Here is my version


2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

---

### Post by Jose Catre-Vandis on 2011-01-26
Let's get down to some command line stuff! Open a terminal.
```
arecord -l
```
should give you a list of capture devices. Here's mine:
```
jose@lynx:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

You could then run a command like this to capture sound from your mic:
```
arecord -d 10 -f cd -t wav -c 2 -D plughw:0,0 foobar.wav
```
This will record 10 seconds, so be ready to talk when you press enter :)

plughw:0,0 -> from card0 device0

It may be that ubuntu/pulseaudio doesn't like your laptop, so you could always uninstall pulse and just use alsa. Out of interest, do the headphones work alright, and turn off the speakers when you plug in.

---

### Post by harkumar on 2011-01-26
you can change the settings in pavcontrol.

---

### Post by cancer10 on 2011-01-26
> **Jose Catre-Vandis said:**
> Let's get down to some command line stuff! Open a terminal.
```
arecord -l
```
should give you a list of capture devices. Here's mine:
```
jose@lynx:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

You could then run a command like this to capture sound from your mic:
```
arecord -d 10 -f cd -t wav -c 2 -D plughw:0,0 foobar.wav
```
This will record 10 seconds, so be ready to talk when you press enter :)

plughw:0,0 -> from card0 device0

It may be that ubuntu/pulseaudio doesn't like your laptop, so you could always uninstall pulse and just use alsa. Out of interest, do the headphones work alright, and turn off the speakers when you plug in.

I dont use the headphone. I am trying to use the built-in mic in my lappy.

I will give your solution a try when I reach home and will update the output.


Thanks for your time.

---

