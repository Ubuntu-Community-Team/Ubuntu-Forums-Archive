---
title: "Sound Problem"
date: 2006-05-10
forum: General Help
---

### Post by dion on 2006-05-10
I have completed installation of breezy, however I have a problem with getting the sound to work.  I have a pentium 2 with onboard sound which uses a soundpro chipset.  I have googled for a solution on this and it appears this card was troublesome even for windows users as the manufacturer didn't place much emphasis on ensuring their were drivers available for the hardware.  
I have tried running alsaconf at the terminal window but alsa does not find any sound cards.  I have tried a couple other distro to check if any of them would find this sound card.  Mandrake provides 2 commands for setting up the sound, alsaconf didn't work in this distro either, but when I ran sndconfig at the terminal and chose soundblaster 16, the card then worked fine. 
Is their any way to do this in ubuntu or any solution for this problem other than purchasing another sound card.

---

### Post by Sutekh on 2006-05-10
I'd suggest you start heree

[ALSA - Soundcard Matrix](http://www.alsa-project.org/alsa-doc/)

To see if you can find your soundcard.  If you can determine the exact model of the onboard sound, you can find out what support ALSA has for it.

You could also start by looking to see what Ubuntu thinks your card is and what modules it currently is trying to use (if any)

```
lspci | grep -i audio
```
```
lsmod | grep snd
```

---

### Post by dion on 2006-05-17
I tried both these commands and nothing happens.  I even tried sudo and the the command and still no joy.  Is it not possible to runf sndconfig in Ubuntu?

---

