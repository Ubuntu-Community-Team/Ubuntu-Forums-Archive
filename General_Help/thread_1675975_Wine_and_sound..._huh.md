---
title: "Wine and sound... huh?"
date: 2011-01-26
forum: General Help
---

### Post by glibdud on 2011-01-26
I've had some intermittent issues with sound in Wine. I was using the "official" Ubuntu Wine repository, and occasionally was having problems with Left 4 Dead dropping sound between the title screen and loading a scenario. I was satisfied with just restarting when that happened, but last night I decided to try EVE Online again, and I had all sorts of new sound issues there. After a little research, I decided to try the c-korn PPA ([https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)) version of Wine with PulseAudio support built in. Here's the play-by-play:

1. Added c-korn PPA and disabled the "official" PPA (probably not necessary).
2. Moved .wine/* to a backup location.
3. "Completely Removed" wine1.2.
4. Installed wine1.3.
5. On a clean install, went into winecfg, saw that PulseAudio was now an option, selected it, clicked "Test Sound", and got the expected sound. Great.
6. Copied my backed up .wine/ back into place and ran winecfg again. Changed the sound to PulseAudio again, applied, hit "Test Sound". The sound was there, but it sounded staticky and awful. No big deal, there's only a couple of things I run under Wine; a clean reinstall is no biggie.
7. Cleared out .wine.
8. Ran winecfg. Selected PulseAudio, applied, hit "Test Sound".

"Audio test failed!"

9. Huh? Ok, start fresh again. Deleted .wine, "Completely Removed" wine, rebooted for good measure, then installed wine again.
10. Ran winecfg again.

"Audio test failed!"

...

I don't get it. How did it work before, and now it suddenly doesn't work, even from a completely fresh install? Is there something somewhere that survives even a "Complete Removal" that could be horked up? Any suggestions welcome.

Running 32-bit Maverick.

---

