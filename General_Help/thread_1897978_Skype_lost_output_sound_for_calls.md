---
title: "Skype lost output sound for calls"
date: 2011-12-20
forum: General Help
---

### Post by pwabrahams on 2011-12-20
I'm running Kubuntu Oneiric, fully updated.  A week ago I was able to get output sound when I made a call with Skype.  Now I can't, although Skype itself hasn't been updated since Natty.  Interestingly, in the Skype forums someone has reported the same problem with xubuntu. That leads me to think that the problem is not with Skype at all but with some system component that was recently updated.  Other than phone calls, my sound is working; in fact, Skype itself can produce the test sound.  If I make a test call, however, I hear nothing -- not even the ringing.

How can I track this down?

---

### Post by pwabrahams on 2011-12-20
The trick is to bring up the Pulseaudio Volume Control, either via Skype or independently, and go to the Playback tab *while a call is in progress*.  In that case an extra line for Skype shows up on the Playback tab.  Skype must be unmuted on that line.  So it's possible to fix the problem only while a call is in progress.  Who would have known?

---

