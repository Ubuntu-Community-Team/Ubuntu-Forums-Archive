---
title: "Audacity Multi-Track Editing?"
date: 2010-06-30
forum: General Help
---

### Post by Joseph Schwenker on 2010-06-30
I keep trying to use Audacity to edit multiple tracks, but it just isn't working for me.  I keep having to go to Jokosher, but then I can't do anything with the audio.  In Audacity, if I try to remove some silence on one track, Audacity automatically selects whatever's on the other track, and does not allow me to deselect it.  This is extremely annoying, as I cannot edit any audio.  To reproduce the problem:

Install Audacity from the Lucid repos
Import an audio file into Audacity
Import another audio file into Audacity
Select some audio on one track
Note how the other track has the same thing selected with chains on it
Press delete
Note how the selection on both tracks was deleted

How can I stop this?

---

### Post by Joseph Schwenker on 2010-06-30
Ah, figured it out.  If you click on Tracks in the menu bar, then uncheck "Link Tracks", you can edit the tracks independently.

---

