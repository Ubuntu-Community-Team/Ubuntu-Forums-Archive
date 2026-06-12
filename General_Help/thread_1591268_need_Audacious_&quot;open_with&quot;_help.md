---
title: "need Audacious &quot;open with&quot; help"
date: 2010-10-09
forum: General Help
---

### Post by Grizool on 2010-10-09
I recently managed to compile and install audacious 2.4.0 successfully. 
I prefer to browse my music folders and double click on the song I wish to play rather than use "open files" within audacious. It works fine to open the first mp3 but when i click to play another song instead of stopping the first one, it opens another instance of audacious and now both songs are playing. When i go into the properties of an mp3 and select open with > "other application" > audacious then click "Use a custom command" the following is in the box /usr/local/bin/audacious %f. is there any custom command I could use so that when I click another song audacious stops the currently playing song and plays the new one, without opening another instance? thanks.

---

### Post by Jose Catre-Vandis on 2010-10-09
Wow - I didn't think you could get multiple instances of Audacious running, this was a feature I have been looking for! I'll have to upgrade.

Check in Preferences, there must be an option to turn off multiple instances?

or In Preferences / Playback, tick Clear Current playlist when opening new files?

I have a custom action to enqueue files for Audacious

Here is the command:
```
/usr/bin/audacious2 --enqueue %F
``` adjust this to suit your system

---

### Post by mc4man on 2010-10-09
You can have 3 variations, all useful in their own way

Load to Audacious (loads and plays, leaves current playlist if any

audacious2 -e -p

New in Audacious  (creates new temp playlist, plays

audacious2 -E -p

Enqueue in Audacious (adds to current list

audacious2 -e

---

