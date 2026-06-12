---
title: "cheese(webcam app) not working"
date: 2010-07-15
forum: General Help
---

### Post by orky7 on 2010-07-15
hi when i installed it, it was work but today after a gap of some days when i open the application the webcam light is on but no video/output is shown in the application when i take a picture it takes it 3-2-1 and then the take a photo button also get deactivated...so how to fix it

---

### Post by orky7 on 2010-07-15
with camorama (another webcam app) the error is "it cannot connect to /dev/video0"...

is this problem is same for cheese also since cheese shows no error but a blank application, with all the options(edit help etc)

---

### Post by NFblaze on 2010-07-15
So it worked before to capture video and take photos, then stopped working some days later?

---

### Post by no2498 on 2010-07-16
gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope that helps if not post back

---

