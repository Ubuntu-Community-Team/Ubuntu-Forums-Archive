---
title: "Gigabyte TV card... where do I start?"
date: 2010-04-14
forum: General Help
---

### Post by Chris Psycho on 2010-04-14
So the only reason I kinda use windows is for games and my dad watches tv...
I hardly play games now though... So if I could manage to get the TV working with ubuntu that would be AWESOME =)...

Please bare with me I am a noob.

Ok... Well first of all:
Its a 
Gigabyte [COLOR=#66B821]GT-PTV-AF-RH[/COLOR]
Tuner: Phillips TDA8275A
Decoder Chip: Phillips SAA7131E

So after googling abit I realised I need mythtv?
Also stumbeled apon: [http://ubuntuforums.org/showthread.php?t=340499](http://ubuntuforums.org/showthread.php?t=340499) (how come I cant reply on that thread?) 
This would be the driver?

Seeing as its the same tuner etc..
1. First do I need to get mythtv first or?
2. How do you create a .sh file? With myth tv?

> You just need to make a tv.sh file in /etc/modprobe.d/
and add this in that file:

 	Code:
 	#!/bin/bash
rmmod saa7134_alsa
rmmod saa7134
modprobe saa7134 card=81 
And make tv.sh script in your /home/USER/ directory to look like this:

 	Code:
 	#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute



All help appreciated!

---

