---
title: "Since upgrade to 9.10 , sound device makes a loud pop sound when opened"
date: 2009-11-09
forum: General Help
---

### Post by kevinlong on 2009-11-09
Ever since I upgraded to 9.10 , whenever I first play a song or if the login sound plays there is a very loud pop/boom sound at the very begining. I am afraid its going to blow my speakers/headphones. Very annoying.. didnt do this in 9.04.

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)


Thank you for looking. :)

---

### Post by kevinlong on 2009-11-09
I think this thread helped solve my issue and it applies to power saving on different soundcards not just intel.

[http://ubuntuforums.org/showthread.php?t=1311262](http://ubuntuforums.org/showthread.php?t=1311262)

> **Kushkah said:**
> The problem is due to your laptop's powersave settings. The pop your hearing is the speaker turning on as powersave has had it off while not playing any sounds. Try this 
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```and change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```to

```
options snd-hda-intel power_save=0 power_save_controller=N
```If that doesn't work for you, you can try
```
sudo echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```as a temporary fix.

---

### Post by antony_css on 2009-11-10
Thanks!

---

### Post by nickbuntu529 on 2009-11-12
> **kevinlong said:**
> I think this thread helped solve my issue and it applies to power saving on different soundcards not just intel.

[http://ubuntuforums.org/showthread.php?t=1311262](http://ubuntuforums.org/showthread.php?t=1311262)
Actually, you dont need to change the "=10" to "=0". Simply put a pound sign and a space in the beginning of the line and save it; log out and log back in. Your sound pop is gone; TADA, an easier method that always works (if not simply completely restart your computer). Also this will work on all soundcards and has been tested to ensure that it will never fail; it was successful...

---

### Post by coffeecat on 2009-11-12
> **nickbuntu529 said:**
>  Simply put a pound sign and a space in the beginning of the line

Pound sign? :? Are you talking about commenting out a line?

On this side of the Atlantic:

Pound sign = £

Hash sign = #

---

### Post by nickbuntu529 on 2009-11-12
> **kevinlong said:**
> I think this thread helped solve my issue and it applies to power saving on different soundcards not just intel.

[http://ubuntuforums.org/showthread.php?t=1311262](http://ubuntuforums.org/showthread.php?t=1311262)
Thought i should say that this is all unnecessary. You only need to put a '#' sign and a space at the beginning of the line and save it then log out and log back in. The sound pop should be gone no matter what sound card you use this has been tested so i know it works because im the one who tested it and this one is permanent. Also, if, after you log out and log back in, the popping is still there, go back and make sure the '#' sign and a space are still there, but this time completely reboot your computer; when you do it'll definitely be gone for good. :)

---

### Post by nickbuntu529 on 2009-11-12
> **coffeecat said:**
> Pound sign? :? Are you talking about commenting out a line?

On this side of the Atlantic:

Pound sign = £

Hash sign = #
i mean a # sign. Sorry I didn't specify

---

### Post by coffeecat on 2009-11-12
> **nickbuntu529 said:**
> i mean a # sign. Sorry I didn't specify

No worries. I guessed you meant that but I didn't want British newbies trying to comment out lines with a £. :p

Useful link:

[http://en.wikipedia.org/wiki/Pound_sign](http://en.wikipedia.org/wiki/Pound_sign)

---

