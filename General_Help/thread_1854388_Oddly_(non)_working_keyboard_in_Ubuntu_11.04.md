---
title: "Oddly (non) working keyboard in Ubuntu 11.04"
date: 2011-10-04
forum: General Help
---

### Post by BasbeestNL on 2011-10-04
Hello everyone, 

Im happily dual booting Ubuntu alongside windows vista for some time now and never had much problems that werent PEBKAC or due to non-supported hardware (soundcard). 

But now i have a problem that is really annoying and to which I can't find a solution. It's about my keyboard. I have a micro$oft comfort curve 2000 v.1.0 keyboard (USB) and this appears to be only randomly working lately. 

That is to say: it works in GRUB, it works in windows, it DOESNT work in the login screen for Ubuntu. Until recently a few reboots or turning it off and on again seemed to do the trick but right now that's not working anymore. I do not get a no keyboard found error whilst booting. Just a completely comatose keyboard when i try to log in. If the keyboard does work in the login screen it will work flawlessly in the rest of Ubuntu, even the multimedia keys etc

I've switched to the ps/2 keyboard that came with my pc, with horrible keys and hope there is a solution to this weird problem!

(what a first post, a question for help. I'm sorry but the problem is annoying and persistent)

---

### Post by kurt18947 on 2011-10-04
Thee was another report of keyboard problems here:
[http://ubuntuforums.org/showthread.php?t=1820951](http://ubuntuforums.org/showthread.php?t=1820951)

I was thinking hardware problem on the other thread but with a second report of a very common problem I'm not so sure.

---

### Post by BasbeestNL on 2011-10-04
well, my issue is almost similar. Except that i also had this problem in older versions (but not persistent enough to bother me). I also doubt that it is a hardware issue given that the keyboard gets detected on startup, works in grub and when i select windows it works there flawlessly...

---

### Post by philinux on 2011-10-04
> **BasbeestNL said:**
> well, my issue is almost similar. Except that i also had this problem in older versions (but not persistent enough to bother me). I also doubt that it is a hardware issue given that the keyboard gets detected on startup, works in grub and when i select windows it works there flawlessly...

It could be an ubuntu kernel problem that is not supporting this keyboard.

Not sure if this will help. Your model is in the support list.
[https://help.ubuntu.com/community/KeyTouch](https://help.ubuntu.com/community/KeyTouch)

Also some comfort of sorts in that you're not alone.
[http://ubuntuforums.org/showthread.php?t=1773653](http://ubuntuforums.org/showthread.php?t=1773653)

---

### Post by BasbeestNL on 2011-10-04
Well if it's a kernel problem, what can i do to solve it. When it works, it works flawlessly...

my mind remains boggled :P

---

### Post by sthadd on 2011-10-12
We fixed this in our situation (keyboard and on screen keyboard not working, but mouse OK)

**Check and see if "Slow keys" is turned on**. (Hit the "guy in the circle" icon in the lower right and choose "Universal Access Preferences" - the bottom option is " Press and hold keys to accept them (Slow Keys))

This just had another programmer and I scratching our heads for a while.

---

### Post by BasbeestNL on 2011-10-13
I'm sorry, but could you clarify please? Slow keys need to be turned on or off? When looking for the guy in circle icon i found i could also explicitly state my keyboard there and did so.

Right now I went for the QuickNdirty solution: my old oem keyboard is in the ps/2 port, and the strangely acting one in the usb port. Sofar i havent had the problem (yet). Offcourse, this is merely treating a symptom.

---

