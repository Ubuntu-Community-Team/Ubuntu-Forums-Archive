---
title: "No sound in Karmic, no Software Center..."
date: 2009-11-02
forum: General Help
---

### Post by Saronn on 2009-11-02
So, today, I installed Karmic. When I restarted, I noticed there wasn't any startup sound. When I went in, the sound was turned all the way up. I just thought it was a little bug or something on first startup. Then I wanted to put on some music, and, of course there wasn't any sound.

Pretty much a few seconds after that, I wanted to see the new Software Center. I looked in Applications, there wasn't anything... I thought maybe it could be in one of the sub-sections, or in System. Both those searches were in vain, as there was no Software Center.

Does anyone know what to do for either of these?

I haven't come across any more bugs, if I do I'll edit.

---

### Post by Saronn on 2009-11-02
Really? Page three after 40 minutes?

Well, I see others are having problems too.

---

### Post by Saronn on 2009-11-06
bump

---

### Post by Saronn on 2009-11-06
I'm really sorry for all the bumps, but I would like at least one person to SAY something...

---

### Post by Saronn on 2009-11-07
another bump.

---

### Post by HardcoreSSG on 2009-11-07
Can't help you about the software center but take a screen shot of your mixer (the sound cards section)

---

### Post by RJ12 on 2009-11-07
is your PCM Muted or turned down low? It seems when I turn the Master Volume up or down nothing happens but when I change the PCM you can hear the difference

---

### Post by Saronn on 2009-11-07
How exactly do I change the PCM? :l

---

### Post by UranUtan on 2009-11-07
Check if there is any silly things like volume has been muted or set to zero. As of today, I have made 1 Xubuntu and 3 Ubuntu installations. There is no sound issue and all the 4 machines are at least 5 years old.

---

### Post by Saronn on 2009-11-07
Under sound preferences, everything is maxed out. Is there anywhere else to change sound options?

---

### Post by Saronn on 2009-11-08
bump

---

### Post by Zoot7 on 2009-11-08
What do you get if you run
```
aplay -l
```

---

### Post by Saronn on 2009-11-08
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by Zoot7 on 2009-11-08
Okay, ALSA sees your sound card. Your issues are more than likely pulseaudio related based on that.
Check out this thread here:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Guell on 2009-11-08
This solved it for me:
[http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio](http://ubuntuforums.org/showthread.php?t=1308237&highlight=pluseaudio)

Turns out pulseaudio couldn't access the audio server because karmic changed rights on my homefolder.

---

### Post by Saronn on 2009-11-10
None of the links worked. Also, I just installed Software Center through the Add/Remove, so I guess it's not a problem even though it was odd it wasn't already installed.

None of my 9.04 CD's work, so, I'm stuck with 9.10. I'm starting to really need sound.

---

### Post by Zoot7 on 2009-11-10
Something to try, install the gnome alsa mixer, add all the channels available and max out everything, if you haven't tried already.
```
sudo apt-get install gnome-alsamixer
```
Sometimes sound issues are just a case of a muted channel.

Failing that, you could try removing Pulseaudio - I wouldn't normally recommend it; it's not the most elegant thing to do as you'll have to rely on the gnome alsa mixer to adjust your volume afterwards. But it'll at least have you fall back to alsa only, which *should* work on account of seeing your card fine:
```
sudo apt-get purge pulseaudio
```

---

### Post by Saronn on 2009-11-10
IT WORKED! REMOVING PULSEAUDIO WORKED!

I dunno how, but, it did. Problem solved :3

---

### Post by Zoot7 on 2009-11-10
Great, good to hear! :)

The only thing I find with removing it this time is that the volume applet no longer will work as it depends heavily on pulseaudio. Also the volume keys of a media keyboard won't work either after that.
Here's a compromise to use the gnome alsa mixer and tie it to the tray - (end of post)
[http://ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntuforums.org/showpost.php?p=8284273&postcount=4)

After removing pulseaudio, I tried recompiling the gnome-applets with the specification to remove pulseaudio support, in the hope I'd get the applet back up and running. 
I was actually able to add a volume applet to the panel despite the lack of pulseaudio, however then... my media keys (play, pause etc.) didn't work, which is a bit of a deal breaker for me.
Alas.. I recompiled them back with the default options, and reinstalled pulse. My only issue with pulse is with flash - I've to stop all audio applications if I want sound from flash (which I can live with), same issue as Hardy before I ripped out pulse, except this time I can't rip out pulse.

Dang! Pulse is pretty integrated this time... :( I hope it's okay come Lucid.
All that said it does show a lot of promise, paving the way towards features like a system wide equalizer which is a feature I've wanted for a long time now.

---

