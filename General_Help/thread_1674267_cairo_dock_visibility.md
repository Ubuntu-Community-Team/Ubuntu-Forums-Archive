---
title: "cairo dock visibility"
date: 2011-01-23
forum: General Help
---

### Post by flipper T on 2011-01-23
i have a cairo dock at the botttom of the screen set to "keep hidden".

previously, when i moved cursor to edge of screen, the dock would pop up on top of the other open windows.

now, for some reason, the dock pops up, but remains below other open windows,

also... when subdocks are displayed, the background is no longer redrawn...dont know why...see screenshot for example.

i dont know the reason for the change, perhaps a change in dock or compiz settings ?

anyway, if anyone knows how to rectify, please let me know,

thx in advance,

---

### Post by flipper T on 2011-01-23
too soon to bump ?

:)

---

### Post by derklempner on 2011-01-23
Go into Coairo Dock's configuration, and make sure you're in simple mode.

On the first tab, Behavior, look for the section titled "Visibility of the main dock".  Change the "Visibility" option to "Always on top", and that should fix your problem.

It may not be possible to auto-hide the dock AND have it pop up on top of other windows.

---

### Post by flipper T on 2011-01-24
hi & thx for responding,

> It may not be possible to auto-hide the dock AND have it pop up on top of other windows

...but that is _exactly_ how it used to behave, only days ago !

i think it might be something to do with compiz (given the lack of bg redraw also ), but i am guessing.

any other ideas ?

---

### Post by flipper T on 2011-01-28
finally solved.

for anyone interested, goto cairo docks config, select system and then composition.

make sure that the "emulate composition with fake transparancy" is un-checked.

childishly happy now :)

---

