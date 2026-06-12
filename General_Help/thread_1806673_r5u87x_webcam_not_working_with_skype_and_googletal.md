---
title: "r5u87x webcam not working with skype and googletalk-plugin"
date: 2011-07-18
forum: General Help
---

### Post by Mauri72 on 2011-07-18
I have an old Sony Vaio VGN FZ18E laptop which has one of these r5u87x webcams
I used Skype in the past on Ubuntu 10.04 but since I updated to 11.04 something has gone screwy with the webcam. The webcam still seems to work on Cheese, guvcview and even on testwebcam.com with flash, but if I try it with Skype or googletalk-plugin I only get a black screen.
I tried all the various tricks of this kind:
export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

and they did not help.
I thought it may be to do with the default resolution, because also Cheese and guvcview show a black screen if I set the resolution to anything higher than 320x240. So I tried to change the Skype config.xml file to set the video capture height and width, but again this did not work. I would try the same on googletalk-plugin but I do not know how to do that.
Any suggestion? any pointer to what the problem may be?
Cheers
Mauri

---

### Post by Mauri72 on 2011-07-18
does anyone know how to set the webcam resolution in googletalk-plugin?

---

### Post by nerdy_kid on 2011-07-18
> **Mauri72 said:**
> does anyone know how to set the webcam resolution in googletalk-plugin?

try  v4l2ucp from the repos, it might work.

---

### Post by Mauri72 on 2011-07-18
Thanks for your reply. I tried it but unfortunately it does not give me the option to set the resolution. What is interesting is that if I start the preview from v4l2ucp, mplayer pops up with a green screen, but if I set the resolution manually with 
mplayer tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0
then the webcam shows well in mplayer too.

how to change that resolution by default? aaargh!!!!!

---

### Post by Mauri72 on 2011-07-21
just to let whoever may be interested in this know that I fixed the problem with Skype by going back to version 2.1
No luck with googletalk-plugin yet.

---

