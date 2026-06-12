---
title: "Touchpad stops responding in mid use - 11.10"
date: 2011-11-14
forum: General Help
---

### Post by Roasted on 2011-11-14
Three different laptops now, all different hardware, I've seen this on... I thought I was just losing all sense of onboard mouse maneuvering until it happened on my Lenovo. My red dot center point in the middle of the keyboard was still able to move the mouse cursor just fine while my touchpad did nothing.

Has anybody else seen this?

---

### Post by whyDerrick on 2012-01-11
Did you have any luck with this? I'm having precisely that issue now on my Lenovo and am working around it with the trackpoint (red dot). It seems random, only happens on occasion and tends to be fixed with a restart, but I'd still like to get to the heart of why it's happening and fix that instead of using a workaround. 

Let me know if you have any ideas or other threads perhaps. I'm very new at this.

From what I've seen people recommend unchecking the "disable touchpad while typing option under "Settings>Mouse & Touchpad > Touchpad" (If you're using 11.10.) To restart the touchpad you can use the terminal command [CODE] synclient TouchpadOff=0 [CODE]. 

Also, here's another link with another suggested fix. [http://ubuntuforums.org/showthread.php?t=1860665&highlight=Touchpad](http://ubuntuforums.org/showthread.php?t=1860665&highlight=Touchpad)

Hopefully this will help you get up and running again (if you're not already).

---

### Post by airplanesimen on 2012-01-11
> **Roasted said:**
> Three different laptops now, all different hardware, I've seen this on... I thought I was just losing all sense of onboard mouse maneuvering until it happened on my Lenovo. My red dot center point in the middle of the keyboard was still able to move the mouse cursor just fine while my touchpad did nothing.

Has anybody else seen this?

Yes, i am actually searching for a sulotion to this problem too. I only have to kill the gnome-session, and log in again, and it works fine for a while, but after a longer while, it just stops responding. Sometimes, the problems starts while i am logging in to my laptop, and it is really annoying.. hope we can find an answer to this problem :P

---

### Post by adityamagadi on 2012-01-11
it is an issue with the gnome shell... just wait for the update.

---

### Post by airplanesimen on 2012-01-11
> **adityamagadi said:**
> it is an issue with the gnome shell... just wait for the update.
okay, lets hope so ;)

---

### Post by Roasted on 2012-01-11
Ironically I've had zero issues with this for quite a while. In fact, I forgot I even posted it. I've even been living on my laptop more as of lately because I'm moving in a few days and my desktop has been packed up for quite some time. *shrug*

---

### Post by grey1beard on 2012-01-11
Just done a clean install of 11.10 on my Toshiba Satellite A30 laptop yesterday, but I have this problem now. 
It did have an occasional "insensitivity" before, so I'm a bit puzzled on how to tell if it's a new problem or the last gasp of the touchpad itself.
Reading the above posts, I'm now going to try the "disable touchpad while typing" option, and see if that improves matters.
....
Well it's frozen on the desktop screen, so now I'm really stuck :(

The keyboard works, but not the touchpad, so it looks like trying a mouse next !

John

---

### Post by whyDerrick on 2012-01-12
If your keyboard works, you can use the terminal command 
[CODE] synclient Touchpadoff=0 [CODE]
That should get it working again. In Unity, you can access the terminal using the keyboard shortcut Ctrl+Alt+T. 

Hope that helps.

---

### Post by grey1beard on 2012-01-12
Thanks whyDerrick.
I'll give that a try next.
Just made an invesment in a new usb optical mouse, and it worked first time. :)
So I now have a fall back position.
Next to get my graphics tablet working ;)
Regards
John

---

