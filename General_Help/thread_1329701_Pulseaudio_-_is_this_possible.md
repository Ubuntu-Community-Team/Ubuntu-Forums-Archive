---
title: "Pulseaudio - is this possible?"
date: 2009-11-17
forum: General Help
---

### Post by blazemore on 2009-11-17
I thought Pulseaudio was supposed to make this sort of thing possible, and it would be so cool if I could get this to work.

I have a bluetooth headset.
I use it to take calls from Skype.

Unfortunately, I have to go into the sound preferences and change the output device to my headset, then mute my music, and THEN take the call.

Is there anyway way that when Skype rings, all other audio can be muted and the Skype call can be router through the headset?

---

### Post by hellmet on 2009-11-18
Not sure if its still around, but I used to use Pulse Audio Switcher when I was using a USB headset. That way, I'd always get calls on my headset.

---

### Post by blazemore on 2009-11-18
Where can I find this program? Google returns nada.

---

### Post by hellmet on 2009-11-18
Sorry, got the name wrong. Its PulseAudio Device Chooser. Its in the repos. I hope it still works like it used to. What with all the development going with PA.

---

### Post by blazemore on 2009-11-18
I have this installed. How can I make it so Skype goes through my headset?

---

### Post by Chronon on 2009-11-18
You should be able to set the output device in Skype preferences, I think.

Ear Candy is another option for automatically fading between different applications.  I think it can do the auto-fadeout bit, at least. [http://ubuntumanual.org/posts/235/earcandy-is-the-next-cool-thing-you-want-in-linux-if-you-are-a-media-buff](http://ubuntumanual.org/posts/235/earcandy-is-the-next-cool-thing-you-want-in-linux-if-you-are-a-media-buff)

---

### Post by Andreas1 on 2009-11-18
if i understood right, you could use *pavucontrol*. it lists all audio streams and devices and allows for them to be redirected.
EDIT: and in my experience it remembers application-specific settings, like skype going to usb headset instead of onboard/whatever

---

