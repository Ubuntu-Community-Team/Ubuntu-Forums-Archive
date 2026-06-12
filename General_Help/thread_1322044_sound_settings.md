---
title: "sound settings"
date: 2009-11-10
forum: General Help
---

### Post by rudi009 on 2009-11-10
is there any way to change the sound settings  bass,treble etc. because my songs in rhythmbox,movieplayer sound very bad whereas limewire make them sound little bit better.

---

### Post by Giblet5 on 2009-11-10
Yeah, the current mixer is about as lame as it gets...

I'm rigged for 7.1 and Gnome provides one single volume slider.

Bring up a terminal window and enter ```
alsamixer
```

You can unMute the "Tone" switch and then you can tweak bass and treble.

---

### Post by Incubus9 on 2009-11-10
I think what you're referring to is an Equalizer. An Equalizer lets you tweak the individual frequencies to "shape" the sound to your taste. A lot of music players have this feature. I see that neither RhythmBox or Movie Player have an Equalizer. My favorite media player is VLC. It has an Equalizer along with other Effects and Filters. Really neat stuff to mess around with.

And as for Alsamixer, the audio devices will vary from one computer to another. I don't see anything for tone there.

---

### Post by rudi009 on 2009-11-10
where is the tone button???

---

### Post by Giblet5 on 2009-11-10
You might not have one. What's there is dependent on your sound chip's capabilities.

Another option that I use is gnome-alsamixer.

```
sudo apt-get install gnome-alsamixer
```

It provides the same access as the text-based alsamixer, but in a gnome gui.

---

### Post by Giblet5 on 2009-11-10
> **Incubus9 said:**
> I think what you're referring to is an Equalizer. An Equalizer lets you tweak the individual frequencies to "shape" the sound to your taste. A lot of music players have this feature. I see that neither RhythmBox or Movie Player have an Equalizer. My favorite media player is VLC. It has an Equalizer along with other Effects and Filters. Really neat stuff to mess around with.

And as for Alsamixer, the audio devices will vary from one computer to another. I don't see anything for tone there.

Yes! That!

But if you like RhythmBox (and I do), the basic tone controls (bass/treble) are adequate (good speakers - front/rear channels are JBL 4673 pro-series cinema speakers, modded for 40hz rolloff - I can thump the smug off a cat.)

---

### Post by Incubus9 on 2009-11-10
I just ran a search on google for rhythmbox equalizer, and it looks like it is or was a legitimate plug-in. That may be worth looking into.

---

