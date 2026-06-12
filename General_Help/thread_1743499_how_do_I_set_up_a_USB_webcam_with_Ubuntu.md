---
title: "how do I set up a USB webcam with Ubuntu?"
date: 2011-04-29
forum: General Help
---

### Post by AdaltrudeVaisbutas on 2011-04-29
I've recently just changed from Windows 7 to Ubuntu yesterday, so as you can understand, I know very little about it AT ALL.
My problem is I have a built in webcam on my laptop that doesn't work very well visually, so I usually use a USB one instead, however I'm not entirely sure how to: 
1. Get the web cam to work, as when I try it with cheese etc. Nothing comes up.
2. how to stop Ubuntu automatically choosing my built in webcam.

My webcam is a CANYON one, and even when I was using windows I had to download a driver for it, so I'm not entirely sure how to go about this at all....

any help really appreciated!

---

### Post by cmorrow132 on 2011-04-29
In Cheese, go to edit/preferences. first, be sure you can modify the Device dropdown. If you can't it's not detecting your webcam. If you can, see if a secondary option is available. If those don't work, you'll have to find a camera that works with ubuntu (google).

---

### Post by cmorrow132 on 2011-04-29
Forgot to mention, go to Administration/Additional drivers and see if it shows that it detected a 3rd party driver for your camera.

---

### Post by no2498 on 2011-04-30
click applications accessories terminal
in the terminal type webcam click enter
after it stops type dmesg click enter

after it stops type lsusb click enter
should give you a number and name for 1 or both cams

in the terminal type gstreamer-properties click enter

click video  you can change the cam you like to use here
try v4l and v4l2
use the bottom test button for each 1

---

