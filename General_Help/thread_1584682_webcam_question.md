---
title: "webcam question"
date: 2010-09-29
forum: General Help
---

### Post by delogren on 2010-09-29
Howdy,

Today I decided I needed to hook up an old, cheap, webcam to the ubuntu laptop.

After installing luvcview I gave it a shot.  No joy.  Here's the error message:


luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
ERROR: Requested frame format MJPG is not available and no fallback format was found.
 Init v4L2 failed !! exit fatal


I'm guessing that the old webcam is not uvc compatible.
Or do y'all think I missed something?

--del

---

### Post by no2498 on 2010-09-29
type lsusb in a terminal click enter
that should give you the cam name and # for the sensor

---

### Post by delogren on 2010-09-29
> **no2498 said:**
> type lsusb in a terminal click enter
that should give you the cam name and # for the sensor

Done.  It gave me this:

Bus 006 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

So I tried various options for luvcview and still no cigar.

Any clues?

--del

---

### Post by no2498 on 2010-09-29
i just put this in google and got a lot of info

003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

---

### Post by delogren on 2010-09-29
> **no2498 said:**
> i just put this in google and got a lot of info

003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam


Again, no joy.  Just a bunch of bug reports and little specific help..

It works on my wife's Windoze machine, so we have a fall-back plan.  And I've ordered a Logitech webcam that's supposed to be uvc compliant.

--del

---

### Post by no2498 on 2010-09-30
open a terminal type cheese click enter
install it if not installed
try the cam in cheese first
after its installed you can find it in sound & video
cheese webcam booth

most webcam's just work now days

---

### Post by delogren on 2010-09-30
> **no2498 said:**
> open a terminal type cheese click enter
install it if not installed
try the cam in cheese first
after its installed you can find it in sound & video
cheese webcam booth

most webcam's just work now days

That's kinda what I figured from the get-go...

So I bought a Logitech and, voila!  It works fine.

Thanks for holding my hand while I came to the realization that my first guess about what was wrong, was right..

Now, it's off to playing with the new Ubuntu toy.

And take a look at cheese....
--del

---

