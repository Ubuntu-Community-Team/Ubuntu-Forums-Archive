---
title: "Webcam help"
date: 2012-03-15
forum: General Help
---

### Post by sedan374 on 2012-03-15
I am using Ubuntu 11.10, and my webcam seems to be giving problems. The actual webcam works (at least when I use Cheese), when I click webcam I can see myself in it. However when I try video chatting with someone on gmail they cannot see me. It gives them a black screen. But I can see myself and them. This happened to multiple people I tried chatting with.

Also when I tried video chatting with aMSN messenger it says my webcam could not be found. 

Any help on how to overcome these problems is really appreciated. Thanks.

---

### Post by sedan374 on 2012-03-16
Bump

---

### Post by sedan374 on 2012-03-17
Bump

---

### Post by Dude-PWB- on 2012-03-18
When you say gmail, are you talking about the gtalk plugin in firefox or are you using pidgin or empathy for gtalk?

I can't say for sure, but i don't think video chat for gtalk is working in ubuntu/linux at the moment. At least I have never gotten it to work. I have not tried it in msn, so I can't speak to that.

If the camera works fine in skype or ekiga, i think that would be the case.

---

### Post by Dragonbite on 2012-03-18
If you are trying to use a program, such as Empathy or Skype, and your webcam does not show the video try this
```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
You can replace "skype" with whatever program you want to have it run.

If you are running it through a browser, then I am not sure if this would work or not.

---

### Post by fragos on 2012-03-18
Make sure you've installed the Google Talk Plugin. If you go into Gmail settings for Chat you'll be offered some configuration options specifically for video chat and a facility to insure they're working correctly.

---

