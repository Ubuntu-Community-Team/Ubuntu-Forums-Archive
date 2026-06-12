---
title: "Sound problem"
date: 2010-01-12
forum: General Help
---

### Post by Steveturner on 2010-01-12
Hello everybody,

I currently have the latest version of Ubuntu, got it yesterday night, and spend nearly all night trying to fix the sound that I could never get fixing.
Now keep in mind that I'm really nooby at Ubuntu.
I don't remember exactly what I did this morning, but I basically got my sound drivers to be restored to defaults, because I don't know why, but for some reason it was saying that it couldn't detect my soundcard, even though when I had **just** installed it, it could detect my soundcard.

It currently can detect my soundcard, but the main problem is that I have sound on RuneScape (Java game for Firefox), but don't have any sound on Flash stuff like YouTube, and no sound when I play an audio cd either. :sad:

I have the latest version of Ubuntu, I'm on a laptop, and when I do get sound, I can get it on both my onboard audio speakers, and on my headset.

I also can't use my mic.



EDIT:

I found out something!

Alright, basically, when I play music on a program called TeamSpeak (3 to be exact), it'll play out my microphone, all of the music, but yet I can't actually hear the music.

Basically, my mic is my speaker, and my speaker is my mic.... but I don't know how to switch them around. Anybody else know...? I'm so glad the problem seems to be simpler.

Hope this helps, to whoever helps me. :smile:

It's not a problem with alsamixer or pulseaudio, I've already been helped on those, as 2 ppl on the Ubuntu irc already helped me with that and it didn't help any. (I've also ready the sticky on here about how to fix common audio problems but it didn't really help)

---

### Post by Steveturner on 2010-01-12
bump

---

### Post by Steveturner on 2010-01-12
Nobody can/wants to help? :(

---

### Post by byStanderone on 2010-01-12
...ey, i'd assume you are in karmic, visit this ubunguide:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

---

### Post by Steveturner on 2010-01-12
Thank you, I'll be checkin' it out, yeah, I think I said latest version of Ubuntu, that's Karmic, my bad.

---

### Post by Steveturner on 2010-01-12
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Sound](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Sound) doesn't help me very much.

If I click on the speaker at the top-right and go to Sound Preferences, I have no Hardware or Input devices to select from, it's completely blank. But I do have an Output devoice to choose which is only 1, "Dummy Output" Stereo.

:(

---

### Post by Steveturner on 2010-01-12
Problem solved, a person on the Ubuntu irc helped me.

It was a permission problem, sudo adduser (username) audio

---

