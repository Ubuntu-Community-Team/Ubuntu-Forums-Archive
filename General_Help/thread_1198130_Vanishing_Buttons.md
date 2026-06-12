---
title: "Vanishing Buttons"
date: 2009-06-27
forum: General Help
---

### Post by dave collin on 2009-06-27
Hi,
When moving mouse pointer over "radio" buttons such as edit, save etc, the writing in the button disappears. It comes back if I move the window, or jiggle the pointer over the button. (see attached screenshot- 3 buttons missing writing).
This only happens in Openoffice apps.
But I've been on OO forum and no answers except that when googling a couple of days ago I saw something similar with KDE installation. Can't find again except that it said something about a graphics card issue and had a work around/fix.
Any suggestions?
(Running Jaunty 9.04 with Openoffice 3.1.0, nvidia ge force 8400M G, driver 180.44 - all the latest with all updates).
thanks
Dave

---

### Post by QIII on 2009-06-27
I don't see it in 3.0.

OOo bug?

---

### Post by kixome on 2009-06-27
It may be the version of java you are using try
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin
sudo update-java-alternatives -s java-6-sun
then run OOo

---

### Post by kixome on 2009-06-27
Is it only in OOO? If not it could be a theme or graphics card issue

---

### Post by QIII on 2009-06-27
Kixome, you bring up an interesting point...

The JRE available in the repositories is Update 13, I believe.

I think Sun's current update is 14 (maybe 15 by now).

Maybe OOo 3.1 is best suited for Update 14?

---

### Post by dave collin on 2009-06-27
Just installed the Java as recommended above by kixome and it's still the same. Oh well.
Also, yes it's just OOo. (All apps. from OOo). The OOo forums said to update from 3.01 (ubuntu release) to 3.10 (OOo) release. I did that yesterday. This made no difference either.
OOo people said possibly graphics card as well. I had a look at nvidea settings in System-Display fiddled with a few obvious things but nothing changed - not game to play with some settings.
Any other suggestions?

---

### Post by dave collin on 2009-06-27
More info.
I've been playing around.
If I change visual effects in "Appearance" to "None" it fixes the problem.
Both "Normal" and "Extra" have the problem.
Also, in "Normal" and "Extra" the writing disappears right when the very tip of the pointer hits the box and the box changes colour slightly. I've been moving the pointer very slowly and it does it every time the box changes colour.
Any ideas now?

---

### Post by dralcohen on 2009-08-04
I have the same problem.  I've attached a few examples.  I tried updating java as suggested. Didn't help. It happens with the default theme and a couple of the others that ship with ubuntu.  I haven't tried any others.  I'm using a GeForce 9800 GT video card. It only happens in open office (v3.0.1). Reducing visual effects to none seems to help.  It was an Ubunutu 9.0.4 fresh install.

---

### Post by dave collin on 2009-11-01
An update - doesn't do this in Karmic.

---

### Post by dave collin on 2010-02-09
Fixed for me - I went back to the "173" Nvidea driver -not the recommended, later version one.

---

