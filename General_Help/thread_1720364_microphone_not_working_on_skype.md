---
title: "microphone not working on skype"
date: 2011-04-03
forum: General Help
---

### Post by joelkhayad on 2011-04-03
I'm using ubuntu 10.10 maverick, i have installed gnome alsamixer and pavucontrol, checked the settings but still not working..I appreciate any help. My laptop model is sony vaio vpcs111fm. thank you.By the way here s d link for my alsa [http://www.alsa-project.org/db/?f=762138d0328f2024b1a3f40a09a1fd142d1e99cc](http://www.alsa-project.org/db/?f=762138d0328f2024b1a3f40a09a1fd142d1e99cc).

---

### Post by stoian on 2011-04-03
I had no microphone signal from my web camera under Skype, until I went into System > Preferences > Sound. In that dialog, switch to input tab and "Choose a device for sound input": I set mine to my webcam (VF0610 Live! Cam socialize HD Analog Mono").

Solved, now, eh?

---

### Post by techunit on 2011-04-03
> **stoian said:**
> I had no microphone signal from my web camera under Skype, until I went into System > Preferences > Sound. In that dialog, switch to input tab and "Choose a device for sound input": I set mine to my webcam (VF0610 Live! Cam socialize HD Analog Mono").

Solved, now, eh?
That may work but I am sure that he has looked over those menus meticulously before posting.

I would open a terminal window and type

```
alsamixer
```

use the arrow keys to move over to your mic and use the up arrows to unmute it. Thats likely your problem.

---

### Post by p110011 on 2011-04-03
I would open a terminal window and type

```
alsamixer
```

use the arrow keys to move over to your mic and use the up arrows to unmute it. Thats likely your problem.[/QUOTE]

If it's muted you have to hit the m key, arrow up to adjust the level.:)

---

### Post by joelkhayad on 2011-04-03
I've tried this one but still its not working

---

### Post by joelkhayad on 2011-04-03
the problem with my input tab is that i have only one sound input and that is the INTERNAL AUDIO ANALOG DEVICE. tnx

---

### Post by Jouke74 on 2011-04-04
In case you have an Intel soundcard and you have not messed with Pulse audio yet:

> First suspend and resume (I know this sounds crazy, but if the soundcard has not been in use for some time, it might go into powersaving mode, same problem here on my netbook).

> Set Skype to use Pulse audio in & output.

> Make sure your speakers + headphone are unmuted.

> (Install pavu control) Open the program.

> Click on input devices .

> Unlock the two microphone sliders so that you can move one and not the other. Make sure they are also unmuted.

> Move the left to full 100% and the right to base (very little).

> Check if there is any signal (the indicator bar below should start moving). Note that as soon as you use any volume control with alsa mixer (Gnome panel), you need to redo these steps. I normally keep pavucontrol op next to Skype to control volumes.

---

