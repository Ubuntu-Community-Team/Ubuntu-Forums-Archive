---
title: "Logitech Quickcam Webcam Goes Dim After Several Seconds"
date: 2011-09-18
forum: General Help
---

### Post by Joseph Schwenker on 2011-09-18
I've been having a problem with my webcam for a long time in Ubuntu where when I open an application like Cheese or Gmail's video chat plugin the video feed will appear fine for several seconds before becoming extremely dim, almost to the point where one cannot see anything in the shot. My webcam is a Logitech QuickCam. Does anyone know of a fix for this?

---

### Post by coldraven on 2011-09-19
Try this, install guvcview from the Software Centre.
Close all other web-cam apps.
Run guvcview and crank up the brightness, then quit, no need to save anything.
See if your other application now works.

---

### Post by Joseph Schwenker on 2011-09-19
Thanks so much! Though the problem wasn't with brightness, you set me along the right path to solving my problem. In guvcview, there is an option in the first tab that says "Auto Gain". I unchecked this box, and my camera stopped "fixing" the light automatically. Thanks for your help!

---

### Post by Joseph Schwenker on 2011-10-18
Though disabling "Auto Gain" in guvcview solves my problem, it only does so temporarily, as I've just learned. As soon as I restart my computer, Auto Gain is enabled again. Is there a way to force this setting?

---

### Post by no2498 on 2011-10-19
install v4l2ucp
after installed it comes up in system/preferences as videoforlinux control panel
i hope it helps you

---

### Post by Joseph Schwenker on 2011-10-20
Unfortunately, that didn't fix my problem. After a reboot, Auto-Gain was checked once again.

---

### Post by no2498 on 2011-10-21
if you click reset or update it will go back to being on

---

### Post by Joseph Schwenker on 2011-10-21
I clicked that button after I unchecked Auto Gain, but when I reboot my computer, it's checked again. Additionally, clicking on update or reset did nothing to change the checked state.

---

### Post by no2498 on 2011-10-22
best i can say is it should have stayed
now im at a loss of what to do 
i hope you get it fixed

---

### Post by oldtimer7777 on 2011-11-27
> **Joseph Schwenker said:**
> bump

When this happens, we call this "snake eyes". End of the road. Time to get some new hardware. Gotta pay to play.:guitar:

---

### Post by coldraven on 2011-11-28
It's me again!
About that tip about guvcview that I posted earlier.
When I first saw it there was mention of doing the uvcview thing instead of setting some command line parameters somewhere. Unfortunately I cannot remember what they were :(
I will have a search of my zillion bookmarks and get back to you.
Stay calm :)

---

### Post by Joseph Schwenker on 2011-11-28
> **coldraven said:**
> It's me again!
About that tip about guvcview that I posted earlier.
When I first saw it there was mention of doing the uvcview thing instead of setting some command line parameters somewhere. Unfortunately I cannot remember what they were :(
I will have a search of my zillion bookmarks and get back to you.
Stay calm :)

Might [this]("http://www.techytalk.info/webcam-settings-control-ubuntu-fedora-linux-operating-system-cli/") be what you're looking for?

---

### Post by coldraven on 2011-11-28
Yes, something like that. Did that not fix it?
I just found this here [http://guvcview.sourceforge.net/](http://guvcview.sourceforge.net/)
but I have not tried it.
> You can also use guvcview (since version 0.9.9) has  a control window only, (from console: guvcview --control_only), this  allows image  control on other apps, like ekiga, cheese, mplayer, skype, ...

---

### Post by Joseph Schwenker on 2011-11-28
I followed the instructions in that article with only slight deviation: I did not modify init.d. I put the command into Startup Applications instead. This is the command to temporarily disable auto-gain, in case that article is deleted in the future:

```
v4l2-ctl --set-ctrl auto_gain=0
```

I'll post again after a reboot.

---

### Post by Joseph Schwenker on 2011-11-29
It worked! Thanks for all of your help.

---

