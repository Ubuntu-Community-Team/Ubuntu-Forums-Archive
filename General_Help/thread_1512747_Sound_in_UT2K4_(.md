---
title: "Sound in UT2K4 :("
date: 2010-06-18
forum: General Help
---

### Post by ownaginatious on 2010-06-18
So every time I try to start Unreal Tournament 2004 with firefox or anything open that uses the sound card, I'm greeted with the following message in the terminal, and no sound:

```
open /dev/[sound/]dsp: Device or resource busy
```

I'm guessing this is because rather than accessing the system's sound mixer, the game is trying to access the sound hardware directly.

Is there a way to make it go to the sound mixer like everything else? The only option in the game settings is "OpenAL".

Thanks!

---

### Post by ownaginatious on 2010-06-22
Bump...?

---

### Post by ownaginatious on 2010-06-23
Awesome, I found the solution in another thread elsewhere. The trick is to launch the application in the following way:

```
aoss ut2004
```

This forces the audio output to the ALSA mixer.

Thought it may be useful to anyone ever searching for the solution to this problem in the future :D.

---

