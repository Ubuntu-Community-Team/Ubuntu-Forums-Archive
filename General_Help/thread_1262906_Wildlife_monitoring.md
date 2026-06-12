---
title: "Wildlife monitoring"
date: 2009-09-10
forum: General Help
---

### Post by Mylorharbour on 2009-09-10
We have occasional visits from badgers in our back garden, usually when we're fast asleep but just occasionally before we go to bed.

Now I have an Ubuntu equipped PC and a Logitec webcam. I presume to monitor them I'd need some sort of motion sensing recording software and perhaps an infrared lamp. Does anyone know of a linux app I could use? Could it turn on the lamp? Would I even need the lamp?

Thanks guys

---

### Post by tgalati4 on 2009-09-10
tgalati4@tpad-Gloria7 ~ $ apt-cache search zoneminder
zoneminder - Linux video camera security and surveillance solution
mythzoneminder - view status and display footage recorded with zoneminder

If you want high-quality pictures to amaze your friends, try hooking up a canon powershot camera and using the remote picture-taking utilities.

---

### Post by StuartN on 2009-09-10
A standard USB webcam has very poor resolution, so images of wildlife will not be great even if you are dedicated / luck enough to get the exact location right. You need the longest USB extension cable you can find, and a rainproof cover.

An infrared floodlight needs to be on all the time you are monitoring, otherwise you can't detect the motion with software. Webcams only work in bright visible light, but you could remove the infra-red filter (a tiny slip of glass over the image sensor).

Standard CCTV cameras might be a better option, with better lenses and IR lamps around the lens for auto illumination at night. You can attach one to a TV card and use it with Zoneminder.

---

