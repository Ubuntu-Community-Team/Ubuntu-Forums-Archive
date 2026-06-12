---
title: "usb mic in ubuntu 9.10 with skype"
date: 2009-11-13
forum: General Help
---

### Post by killthatnoise on 2009-11-13
I can not get my usb mic work under ubuntu 9.10 with skype.

Help would be appreciated. Thanks

---

### Post by killthatnoise on 2009-11-13
uppin :wink:

---

### Post by killthatnoise on 2009-11-13
upping again:frown:

---

### Post by hskprzemek on 2009-11-15
I've got the same problem. My usb mic doesn't work either

---

### Post by gordintoronto on 2009-11-15
Are you using Pulseaudio?

What settings have you tried in Skype/Options/Sound devices?

Have you checked the volume controls to make sure your mic is not muted?

Does your system have any other microphones?

---

### Post by 1Nadie on 2009-11-15
Sorry, to write here, but it looks that usb sound devices are not recognized by Ubuntu at all, I have  Harman Kardom usb speakers and these don't work either..
I was Running version 9.4, upgrade to 9.10 and got the same problem, Btw, in the same machine I got W7 and evething works on 7..
Thanks for Ur Help!!

---

### Post by Chronon on 2009-11-15
The USB audio device in my monitor's webcam works perfectly now in Karmic, for the first time.  It never worked in Jaunty or before.  So, some USB audio is working.  

People should verify that mixer levels are up, proper recording source is selected, PA isn't muted, etc.  "Does not work" is not very detailed.  You should say exactly what you have done and how you can tell it's not working.

---

### Post by gordintoronto on 2009-11-15
> **1Nadie said:**
> Sorry, to write here, but it looks that usb sound devices are not recognized by Ubuntu at all, I have  Harman Kardom usb speakers and these don't work either..
I was Running version 9.4, upgrade to 9.10 and got the same problem, Btw, in the same machine I got W7 and evething works on 7..
Thanks for Ur Help!!

I would bet money that this is just a setting in Pulseaudio.

---

### Post by mo.reina on 2009-11-15
> **gordintoronto said:**
> I would bet money that this is just a setting in Pulseaudio.

totally agree.  i would check skype options and try different devices, i had to play around with mine until i got everything working.

---

### Post by karli on 2009-11-20
Check your settings in System->Preferences->Sound->Input

You may have choosen the wrong device

---

### Post by mdurham on 2009-11-20
> **karli said:**
> Check your settings in System->Preferences->Sound->Input

I don't have "System->Preferences->Sound" on Karmic, which distro are you using?

---

### Post by gordintoronto on 2009-11-21
> **mdurham said:**
> I don't have "System->Preferences->Sound" on Karmic, which distro are you using?

I am running Ubuntu/Karmic, and have Preferences/Sound.  This was a fresh install onto an "empty" hard drive.

---

### Post by mdurham on 2009-11-21
> **gordintoronto said:**
> I am running Ubuntu/Karmic, and have Preferences/Sound.  This was a fresh install onto an "empty" hard drive.
Thanks for that gordintoronto, would you do me a favour please and tell me what program your System->Preferences->Sound menu item launches. You can look with the menu editor.
Cheers, Mike

---

### Post by gordintoronto on 2009-11-22
It's gnome-volume-control.

---

### Post by mdurham on 2009-11-23
> **gordintoronto said:**
> It's gnome-volume-control.

Thanks

---

