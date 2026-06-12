---
title: "Volume control"
date: 2010-08-07
forum: General Help
---

### Post by DeMus on 2010-08-07
When trying to start gnome-volume-control I get these messages:

```
** (gnome-volume-control:16526): WARNING **: Connection failed, reconnecting...
```

I do have sound, I can however not control it. I can not adjust the volume to mention one thing.
I did a fresh install of Ubuntu Ultimate Edition 64 bits.
What can be wrong here?

---

### Post by utilitytrack on 2010-08-07
manage sound levels via [FONT="Courier New"]alsamixer[/FONT]. 

PS
Although I think you know about this :)

---

### Post by DeMus on 2010-08-07
> **utilitytrack said:**
> manage sound levels via [FONT="Courier New"]alsamixer[/FONT]. 

PS
Although I think you know about this :)

Yes, I know that, but that's not the way I had it when I was using the 32-bits version. Why can't I connect to the volume-control? What is wrong here?

---

### Post by DeMus on 2010-08-07
I just noticed that Banshee and VLC produce sound, but movieplayer XBMC does not.
Can somebody please help me to get my sound system like it should be?
Thanks.

---

### Post by DeMus on 2010-08-07
In system monitor now and then I see 1 or 2 entries for pulseaudio. They are there for a few seconds and then they are gone.
In my laptop I see 1 entry all the time, which I believe should be the case.
Who can help me?

---

### Post by DeMus on 2010-08-08
I managed to get sound working in XBMC too, so it seems in all programs sound works.
What does not work is that I can not control the level from the keys on the keyboard. I have to start a mixer program to change volume and that is not what I would like to have. Volume keys have been set in Keyboard shortcuts.
Who has any idea what doesn't work here?

---

### Post by worksofcraft on 2010-08-08
I am running 64 bit Ubuntu 10.04.

On my keyboard is a blue "FN" key and pressing FN and the F4 key increases the volume. Pressing "FN" and F3 decreases volume, FN ands F2 mutes/unmutes. I also have a Panel applet icon and that has a volume slider.

When I play a CD through Rythmbox or a DvD through VLC then all these controls work just as expected... as long as I have selected correct hardware:

The panel applet has a "Sound Preferences" option and that has a tab for hardware and another for output. For my speakers I must sellect USB and for my headset Internal Audio Analog Stereo in BOTH of those.

If I select the wrong combination I still get sound, but the controls do not work. Perhaps you have wrong combination for your hardware?

---

### Post by DeMus on 2010-08-08
> **worksofcraft said:**
> I am running 64 bit Ubuntu 10.04.

On my keyboard is a blue "FN" key and pressing FN and the F4 key increases the volume. Pressing "FN" and F3 decreases volume, FN ands F2 mutes/unmutes. I also have a Panel applet icon and that has a volume slider.

When I play a CD through Rythmbox or a DvD through VLC then all these controls work just as expected... as long as I have selected correct hardware:

The panel applet has a "Sound Preferences" option and that has a tab for hardware and another for output. For my speakers I must sellect USB and for my headset Internal Audio Analog Stereo in BOTH of those.

If I select the wrong combination I still get sound, but the controls do not work. Perhaps you have wrong combination for your hardware?

When I start the gnome-volume-control I get the error messages mentioned in post #1. I can not get to the slider, nor to the preferences at all.
Volume control using up- and down-volume on my keyboard don't function, although I did set them.
In System Monitor I see 2 entries for Pulseaudio flashing in and out, instead of 1 being there constantly.
I checked which programs are started and in the laptop the same programs are started at boot.
I checked which services are running with my laptop, all the same.
With previous distros this used to be okay, with this one it doesn't function. Guess I have to go back to the 32 bit version.

---

### Post by worksofcraft on 2010-08-08
IDK what to look for. I suggest:

System->Administration->System Testing->Audio Tests

You can go back to 32 bit but on my computer 64 bit is working really well, and hopefully someone will know how to make it work for you too :)

---

### Post by DeMus on 2010-08-08
> **worksofcraft said:**
> IDK what to look for. I suggest:

System->Administration->System Testing->Audio Tests

You can go back to 32 bit but on my computer 64 bit is working really well, and hopefully someone will know how to make it work for you too :)

The audio tests work, I did that yesterday already. Well, I go back to the 32 bit version at the moment (am typing this on the laptop).
This just has to work, I am so used to it.
Thanks for your help. Do you also use Ultimate Edition?

---

### Post by worksofcraft on 2010-08-08
Lol, no I had never heard of Ultimate Edition :O
Most ppl on these forums are light years ahead of me. I just use  standard versions of everything until I understand what the difference actually is.

So thanks for that tip! I go research it now. Perhaps I make another partition and have it as alternative boot option.

---

### Post by DeMus on 2010-08-08
Okay, things are working. I did a fresh re-install of Ultimate Edition 32 and had the same problems as with the 64-bits variant. The problem must be somewhere else. Then I thought, can it be my home folder which is still on disk? So, once more a fresh re-install, but now with formatting the home folder as well and now things are OK. There must have been something in one of the settings in the home folder which was responsible for this.
Anyway, things are working again. Thanks.

---

