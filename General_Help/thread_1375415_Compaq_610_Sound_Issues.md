---
title: "Compaq 610: Sound Issues"
date: 2010-01-07
forum: General Help
---

### Post by Bucky Ball on 2010-01-07
Hi all,

New Compaq 610. Sound is working but only through left speaker. Open volume control and PCM and Front BOTH control the sound level, master does nothing.

Strange part is getting stereo but through only the left hand speaker. If I turn down the left slider on PCM and Front, I get the right channel only but through the left speaker. If I turn down right channel I get left channel only through the left speaker.

Weird one. Any help, suggestions, ideas? I have looked at a few sound guides and nothing has worked so far. There doesn't seem to be a comprehensive one for the this particular machine and situation. What I do know though is that sound issues appear to be not uncommon on these machines.

Here's hoping ...

ps: 8.04.3 and headphones work faultlessly. Could be a dead speaker on brand new machine but I doubt that as the problem seems to be that sound is somehow routed only through the left. Left and right channel sound exists but all through left speaker.

---

### Post by Bucky Ball on 2010-01-08
Bump. Still getting nowhere. Any ideas?

---

### Post by Bucky Ball on 2010-01-10
I have tried everything from this page:

[http://ubuntuforums.org/showthread.php?t=109004](http://ubuntuforums.org/showthread.php?t=109004)

... and just about everything else I can find and think of but still nothing. There must be a fix out there somewhere, starting to drive me a bit (more) insane! ;(

---

### Post by Bucky Ball on 2010-01-11
.

Oops. Posted in error.

---

### Post by Bucky Ball on 2010-01-11
I'll keep adding updates and hopefully the penny will drop for me or another user.

```
anna@katie:~$ grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: IDT 92HD71BXX
/proc/asound/card0/codec#1:Codec: Generic 11c1 ID 1040
anna@katie:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name    : 'PulseAudio'
  Components    : ''
  Controls      : 4
  Simple ctrls  : 2
```* Fixed to:

```
anna@katie:~$ grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: IDT 92HD71BXX
/proc/asound/card0/codec#1:Codec: Generic 11c1 ID 1040
anna@katie:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xe8504000 irq 16'
  Mixer name    : 'IDT 92HD71BXX'
  Components    : 'HDA:111d7608 HDA:11c11040'
  Controls      : 17
  Simple ctrls  : 13
```... so now that at least matches. No different after a restart though.

... and I have added this line to the end of my alsa-base file:

```
# Fix Sound 
options snd-hda-intel model=compaq
```

Also this:

```
anna@katie:~$ locate snd-hda-intel
/lib/modules/2.6.24-24-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.24-26-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
```

I have a feeling I need to make sure it is loading first. Maybe its not. Any ideas??

---

### Post by Bucky Ball on 2010-01-11
This is something. When I add the -f (force) option to get the snd-hda-intel module to install first sound dies totally and no devices can be found.

```
# Fix Sound 
options snd-hda-intel model=compaq -f
```I currently have:

```
# Fix Sound 
options snd-hda-intel model=stack3
```It gives me sound but as it was; all out of the left speaker. I figure it has something to do with loading the correct module and model at boot. Hmm. This is tedious.

---

### Post by inzi2u on 2010-03-21
hi,
I dunno if you are still wondering about this One sided sound problem..
but if you pick up the manual n read it.. It says "Integrated Mono Speaker"

here is the link to the book.. 

[http://docs.google.com/viewer?a=v&q=cache:vr3JvGdEd2kJ:h18004.www1.hp.com/products/quickspecs/13304_div/13304_div.pdf+only+left+speaker+working+on+ubuntu,compaq+610&hl=en&gl=lk&pid=bl&srcid=ADGEESgdiU0RMGlQu4CEYi6KzTLZgxvPDlCkm8c-Uv5OrQElsyCG_xgmzpj4k3IrpRboxauzbn2tpDH1NP6lLlo7yTWbNyU4ErBVzfyQNdGF0lMGBIHwsLOC5p7A09KgXi7fWkir8OZy&sig=AHIEtbSO8XBUNF7IziFTDUQnVu8qrodzLg]("http://docs.google.com/viewer?a=v&q=cache:vr3JvGdEd2kJ:h18004.www1.hp.com/products/quickspecs/13304_div/13304_div.pdf+only+left+speaker+working+on+ubuntu,compaq+610&hl=en&gl=lk&pid=bl&srcid=ADGEESgdiU0RMGlQu4CEYi6KzTLZgxvPDlCkm8c-Uv5OrQElsyCG_xgmzpj4k3IrpRboxauzbn2tpDH1NP6lLlo7yTWbNyU4ErBVzfyQNdGF0lMGBIHwsLOC5p7A09KgXi7fWkir8OZy&sig=AHIEtbSO8XBUNF7IziFTDUQnVu8qrodzLg")

---

