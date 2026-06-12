---
title: "Want to use input jack and play sound through my speakers...."
date: 2010-06-10
forum: General Help
---

### Post by Vanillalite on 2010-06-10
I have onboard sound, and have a blue jack that can be used for input sound wise. You can plug a device in and then just play it through your speakers. This works for me in Windows 7, but I'm not sure how to get this to work in Ubuntu.

I went to my sound settings, but didn't see anything to make my input jack active. I'm just basically using my pc as a pass through to play through my pc speakers.

Any help?

---

### Post by ubunterooster on 2010-06-10
```
sudo apt-get install gnome-alsamixer
```
then go to the sound are in your menu and start Gnome ALSA mixer

---

### Post by Vanillalite on 2010-06-10
> **ubunterooster said:**
> ```
sudo apt-get install gnome-alsamixer
```
then go to the sound are in your menu and start Gnome ALSA mixer

Alsa mixer is installed. Don't really see any new options under sound though? Sorry if I seem like such a n00b! Thanks in advance!

---

### Post by ubunterooster on 2010-06-10
So you have the pakage by the exact name "gnome-alsamixer" installed (screenshot 1) yet it does not show up in sound and video (screenshot 2) ?

If it does turn up "line" (screenshot 3 )

---

### Post by Vanillalite on 2010-06-11
Yeah my bad I was looking for a new tab in my sound properties and not under the sound group under applications.

So the program is installed, but I still don't hear anything despite checking the input sources boxes.

---

### Post by Vanillalite on 2010-06-11
Yeah my bad I was looking for a new tab in my sound properties and not under the sound group under applications.

---

