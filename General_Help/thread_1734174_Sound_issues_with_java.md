---
title: "Sound issues with java"
date: 2011-04-20
forum: General Help
---

### Post by marblecatdog on 2011-04-20
Hey, I tried posting this at stackoverflow, but i think its actually not a code problem but a problem some where in my ubuntu setup, so figured I would try here.  Ok, so i've been programming with java for college, and recently we starting working with sound.  Long story short, my laptop uses an external soundcard to replace the poor sounding built in one, and all java programs that have sound refuse to use said external sound card.  And weirdly enough, they play out of my laptop speakers though the internal card, despite that fact that I have that card off in sound settings.  Also, the sound works in openjdk, but not sun java.  I would switch over to openjdk, but a lot of my programs do not run well with openjdk (freezes and such).  I have tried copying the lines in the openjdk sound.properties file that say they allow it to play over pulseaudio to the sun java sound.properties file, and when I do this sun java plays sound, but has the same problems with freezing my java programs and such just like openjdk.  So I'm thinking its a problem with pulseaudio (or something), I googled and got a lot of answers (uninstall pulseaudio, mess with alsa setting etc).  But I was wondering if anyone knows for sure (or has a good suggestion) as too what I should do?  I'm happy to provide any files or information you guys need, thanks!

---

### Post by marblecatdog on 2011-04-20
I've played around with the Alsa configuration file and I've tried setting my USB card to position 0 in the configuration file and I also tried adding my internal audio to the alsa blacklist.  With either of these attempts, java sound works correctly, but after using a java program my soundcard is no longer listed at all (not in sound settings, or pulsesudio setting etc and I can't get sound anymore).  So any way to stop java from taking over/disabling my soundcard, or another solution to my sound issue?

---

