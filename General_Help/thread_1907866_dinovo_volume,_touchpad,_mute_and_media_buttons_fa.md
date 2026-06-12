---
title: "dinovo volume, touchpad, mute and media buttons fail"
date: 2012-01-12
forum: General Help
---

### Post by D0Z on 2012-01-12
Coming from  about 2 years of running Ubuntu 10.04, I'm finding some difficulties with Xubuntu 11.10.

After the rather wel know [fix]("http://awesomelinux.blogspot.com/2010/05/ubuntu-1004-lucid-logitech-dinovo-edge.html") to get the Logitech Dinovo keyboard to work in Xubuntu 11.10, some keys refuse to work.

When using the volume slider and mute button on the keyboard the notify window shows up.
I can get the volume bar moving and the red X appearing in this window but with no further effect.
The actual sound volume is not affected by this. The little mixer icon in the panel does nothing.

I am using an external USB DAC, with ALSA.

What am I missing?

---

### Post by D0Z on 2012-01-13
Bump.

---

### Post by D0Z on 2012-01-14
Anyone have a clue?

---

### Post by D0Z on 2012-01-15
And up again...

---

### Post by s3a on 2012-01-15
I'm not in an Xfce computer right now but if you know which terminal commands do each thing you asked for (like mute, volume up, volume down, etc) you can add them in the keyboard shortcut configuration window (sorry, I don't know offhand where it's located since I'm not a longtime Xfce user) and choose your media keys as the keyboard keys.

Edit: For the sound issue, I think you should try unmuting things using the alsamixer command in a terminal. I have that problem too in my Debian Testing Xfce computer.

Edit #2: Sorry, if my answer isn't spot on, I skimmed your post.

---

### Post by D0Z on 2012-01-17
> **s3a said:**
> I'm not in an Xfce computer right now but if you know which terminal commands do each thing you asked for (like mute, volume up, volume down, etc) you can add them in the keyboard shortcut configuration window (sorry, I don't know offhand where it's located since I'm not a longtime Xfce user) and choose your media keys as the keyboard keys.

Edit: For the sound issue, I think you should try unmuting things using the alsamixer command in a terminal. I have that problem too in my Debian Testing Xfce computer.

Edit #2: Sorry, if my answer isn't spot on, I skimmed your post.

[https://wiki.archlinux.org/index.php/Xfce](https://wiki.archlinux.org/index.php/Xfce)

Search with CRTL+F for "mute" and up comes a list with commands. Many thanks!!

---

### Post by D0Z on 2012-01-18
I just found out that after rebooting and switching of the external sound card (DAC), the solution stated above, does not longer work.

The shortkey settings are still present in the keyboards Application Shortcut menu.

:(

---

### Post by D0Z on 2012-01-20
Bump ...

---

