---
title: "No sound"
date: 2012-09-08
forum: General Help
---

### Post by Foxhound42 on 2012-09-08
Hello. I have recently switched over to Ubuntu. I am in need of help. I was able to hear sounds from my Macbook's internal speakers, but not from earbuds. So, I did a step by step way to fix this, but after I did, no sound came from my computer at all. I do not know how to fix this. I am not completely computer illiterate, but I don't know much about Ubuntu. Please help.

---

### Post by pqwoerituytrueiwoq on 2012-09-08
maybe if we knew exactly what you did...
got a link to this how to?

---

### Post by Foxhound42 on 2012-09-08
[http://ubuntuforums.org/showpost.php?p=9896318&postcount=1](http://ubuntuforums.org/showpost.php?p=9896318&postcount=1)
There's the guide I followed.

---

### Post by pqwoerituytrueiwoq on 2012-09-08
[FONT=Courier New]sudo rm /etc/modprobe.d/alsa-base; sudo reboot[/FONT]
post output of [FONT=Courier New]aplay -l[/FONT]

---

### Post by Foxhound42 on 2012-09-08
Hmm... so I typed it in after doing the first command and got an error saying "applay: invalid option -- '1'
Try 
'aplay --help' for more information"

---

### Post by pqwoerituytrueiwoq on 2012-09-09
try copy/paste that is a lower case L not a one

---

### Post by Foxhound42 on 2012-09-09
Alright, I did that. This is what I got.
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
   Subdevices: 1/1
   Subdevice #0: subdevice #0

---

### Post by pqwoerituytrueiwoq on 2012-09-09
```
speaker-test -c 2 -r 48000 -D hw:0,0
speaker-test -c 2 -r 48000 -D hw:0,1
```
either of those make any noise?

---

### Post by Foxhound42 on 2012-09-09
Neither of those made any noise.

---

### Post by pqwoerituytrueiwoq on 2012-09-10
make sure nothing is muted in alsamizer
```
alsamixer
```
what does this give you
```
lspci | grep Audio
```

---

### Post by Foxhound42 on 2012-09-10
I typed in the command and got this:
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

---

### Post by Foxhound42 on 2012-09-10
I didi the lspci command:
00:1b.o Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

---

### Post by opensshd on 2012-09-10
When you go System Settings --> Sound, does it show an output device there?

Are you sure nothing is muted in alsamixer? use the right and left arrow keys in alsamixer to go through the different channels, there may be more scrolled offscreen that you may have missed ;)

---

### Post by Foxhound42 on 2012-09-10
There is a digital and analog output in the sound settings.
In alsamixer, there is a 100 above each of the little tabs on the bottom, but the bars that have red white and green on them have 00's below them.

---

### Post by opensshd on 2012-09-10
Yah, thats sounds ok - no bars are muted though right? Red white and green with 00's is 100%

---

### Post by Foxhound42 on 2012-09-10
The second bar has nothing under it, the last one has no bar and says "MM" and the two right before it have no bar and say 00

---

### Post by opensshd on 2012-09-10
Can you use the arrow keys and adjust each of the bars? Try increasing the values of "the two right before it have no bar and say 00" to 100% and check the sound.

---

### Post by Foxhound42 on 2012-09-10
I can't adjust them.

---

### Post by opensshd on 2012-09-10
try this:

sudo apt-get install alsamixergui

then hit alt+f2 and enter alsamixergui

see if you can change values in there...

---

### Post by Foxhound42 on 2012-09-10
Well, I installed Alsamixergui, but alt+f2 doesn't do anything... It may have to do with the fact that I'm on a macbook?

---

### Post by opensshd on 2012-09-10
Ok... alsamixergui on the command line will also work.

---

### Post by Foxhound42 on 2012-09-11
Alright... I got to alsamixergui, but I'm a bit confused about it...

---

### Post by opensshd on 2012-09-12
All your doing is adjusting output levels in there. Making sure no output is muted and then testing the sound.

---

### Post by Genkakuzai on 2012-09-12
Hello all,

I've recently installed Ubuntu Studio 12.04 on my Toshia (Satellite P855-S5200) laptop. I'm not able to get sound out of my speakers?

Tell me what to enter into the command & I'll give all the information I can. 

I'm not sure if JACK is doing something or what. I installed Ubuntu Studio so I can play with audio recording and without having speakers it's pretty pointless.

I'm comfortable with linux but not an expert, all help is appreciated!

Thanks.

---

### Post by Genkakuzai on 2012-09-12
When I go to menu>settings>linux audio configuration this is what I get.

"JACK can only be configured with a loaded and stopped studio. Please create a new studio or load and stop an existing one."

I can see a volume icon, which I can click on and go to Sound Settings. It allows me to adjust volume/output. I don't believe anything is muted.

---

### Post by Foxhound42 on 2012-09-12
Every bar in Master is full and the two in Capture are about 2/3 of the way up

---

### Post by opensshd on 2012-09-13
hmm.. I've just reread through the thread... this is a problem I've not encountered - I don't know how much help I can be ><

try purging alsa and configurations and reinstalling maybe?
```

sudo apt-get install --purge --reinstall alsa-base

```

---

### Post by opensshd on 2012-09-13
Saw this as well, perhaps it can work where alsamixergui failed?

[http://www.mguhlin.org/2008/11/sound-not-working-on-mac-headphones.html](http://www.mguhlin.org/2008/11/sound-not-working-on-mac-headphones.html)

I know yours is the opposite problem, but maybe worth trying?

---

### Post by Foxhound42 on 2012-09-13
Still having the problems... tried both of those

---

### Post by Foxhound42 on 2012-09-16
You uh... still there?

---

### Post by opensshd on 2012-09-19
Does the sound work when booting from disk into the LiveOS?

---

### Post by opensshd on 2012-09-20
Also, I came across a neat asla diagnostic script. Try this in terminal

wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

Upload alsa info and paste link here and I'll take another look.

---

