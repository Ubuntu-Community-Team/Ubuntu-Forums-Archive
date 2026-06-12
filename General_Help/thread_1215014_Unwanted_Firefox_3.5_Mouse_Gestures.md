---
title: "Unwanted Firefox 3.5 Mouse Gestures"
date: 2009-07-16
forum: General Help
---

### Post by King_Critter on 2009-07-16
Finally got around to putting Fx 3.5 on my laptop. The problem is that there seems to be some sort of mouse gestures enabled by default. I checked in about:config and disabled everything that had the word gesture in its name, but still no luck.

Here's the gesture: mouse wheel down, then a left click. Since I'm using the touch-pad for both scrolling and clicking, I end up doing this quite often.

The weird bit is, I'm not quite sure what action this gesture is tied to. Most of the time it performs a Foreword action, but other times it takes me to a random site from my browser history. (Example: when I tested out just a moment ago, it took me to the wikpedia page for the new Star Trek movie.)

Note: I don't have any mouse gesture plugins installed, and this happens in both the version I downloaded straight from Mozilla's site and the unbranded version from their PPA.

EDIT: Fixed, I think. I realized that what I was actually doing was accidentally middle clicking. So i checked in about:config and found something called middlemouse.contentLoadURL. I set that to False and it seems to have fixed my problem.

---

### Post by Hobbes on 2009-09-18
Hey Thanks, you're awesome! This was happening to me and seemed so random, searched google and was linked here, I think it is fixed now (*crosses fingers*). :)

---

