---
title: "Sound Card disappeared?"
date: 2011-10-26
forum: General Help
---

### Post by HippieDave on 2011-10-26
Two days ago my MAudio sound card was just fine.  Now the computer doesn't even see it, and I have no sound playback from any source. I am using Ubuntu 10.4 (LLynx)

When I first loaded 10.4, I experienced the usual probs w/ the MAudio card --there was an issue with Lynx not recognizing it.  But there was a work around and I got it working.  Step one in the work around was to use a terminal to ask for a 'aplay -l'to get a list of soundcards.  When I do that now, the PC says it has none.

Second, in the workaround I could bring up a sound panel by typing in 'alsamixer' and fiddle with it to get the sound.  The computer now does not recognize that command.

I would suspect the sound card has died, but when I turn on my desktop speakers (hooked directly to it) I hear a 'pop'.

What's going on?

---

### Post by duke.tim on 2011-10-26
Sounds like Alsa might have been uninstalled. Try installing it
The terminal command would be 
```
sudo apt-get install alsa-base 
```

---

