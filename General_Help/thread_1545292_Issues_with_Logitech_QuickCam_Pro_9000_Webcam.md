---
title: "Issues with Logitech QuickCam Pro 9000 Webcam"
date: 2010-08-03
forum: General Help
---

### Post by StewartM on 2010-08-03
Hello Everyone,

I have two computers--a Zareason machine (no details yet) running 8.04. I also have a Dell 1525N laptop running 9.10.

I purchased recently a Logitech QuickCam Pro 9000 Webcam. The video works on both systems with Ekiga and Cheese. I can also see the video in Flash applications (but *not* in Meebo even with the other person logged into Meebo). (Both computers are running the latest Flash plugins).

However, the built-in microphone is problematic. With 8.04, I get playback when I test it under System|Preferences|Sound--but with lots of echo. But I get no sound with any Flash chat applications. I've not been able to test it with Ekiga as the testee (a Windows 7 user) can't get Ekiga to work on his machine (probable Windows firewall issues). I haven't installed Skype because Skype pulled its 8.04-compliant .deb packages and I've not tried yet to compile it from source code.

With 9.10, the webcam works with Cheese (video) and I can get both webcam and mic to work with Skype. (Again, no test result possible for Ekiga until I get a testee). 

However--my Win7 testee friend says that when I log into Googlechat using Pidgin on my 9.10 laptop, a webcam icon appears next to my userID telling him that I have an open webcam (even when there's **NONE** actually plugged in). He doesn't see the same icon when I log into my 8.04 desktop with no webcam plugged in. I have searched Pidgin and my System preferences and see no evidence that any of these applications or my system sees a webcam that's not there.

So--how to get the mic to work? (I am thinking the simplest answer will be to simply upgrade my desktop to Lucid). And also, why the webcam icon in Googlechat even when no webcam is plugged in on my 9.10 laptop??

StewartM

---

### Post by awoehler on 2010-08-03
I had a similar problem relating to mic's. If you are using Alsa for sound make sure to check Alsamixer (command line) to make sure that your inputs are not muted. Also check System->Preferences->Sound and make sure that the correct input has been selected. As far as upgrading to Lucid, I'm having mouse cursor disappear issues which I haven't figured out yet, so I would hesitate on that.

---

### Post by StewartM on 2010-08-13
I've done the upgrade to 10.04, and gotten the webcam working. So I'll mark this thread as solved.

StewartM

---

### Post by carandraug on 2010-08-29
> **StewartM said:**
> I've done the upgrade to 10.04, and gotten the webcam working. So I'll mark this thread as solved.

StewartM

Hi Stewart. Did you had any problems with the quality of the image? I'm also using 10.04 with logitech webcam Pro9000 but the image looks strange. Not a resolution problem, more choppy and keeps flashing. Did you had to configure anything? Did you made a fresh install of 10.04 or did the updated from 8.04 to 10.04?

---

### Post by no2498 on 2010-08-30
carandraug

all the help you need is in the cheese help FAQ'S

change the plug in

---

