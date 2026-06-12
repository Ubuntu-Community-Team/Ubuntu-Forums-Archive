---
title: "Delay in closing windows"
date: 2009-07-05
forum: General Help
---

### Post by mharrison on 2009-07-05
I am wondering if there is a way to get rid of the delay when closing an open window.  Best example I have is that I will working in any application, I hit the X to close the application and there is a 2-3 second delay before it closes.  

I think this has something to do with compiz because I do not notice this problem in Xubuntu.

I'm currently using Ubuntu 9.04.

---

### Post by Giant Speck on 2009-07-05
Well, if it is being caused by Compiz, you can go to System > Preferences > CompizConfig Settings and click on Animations.  Then go to the "Close Animation" tab and look through those settings.

---

### Post by ivanvajar on 2009-07-05
The easy way is to disable close animation or choose another in System > Preferences > CompizConfig Setting > animations.

---

### Post by HavocXphere on 2009-07-05
Does this sound familiar:
[https://bugs.launchpad.net/bugs/351186](https://bugs.launchpad.net/bugs/351186)

Also, there is a solution towards the end of the comments, but I haven't tried it myself.

---

### Post by Nevart on 2009-07-05
You can disable the animations completely by going to the display set up and picking "none" off the list.

Since you've upgraded from Xubuntu, you probably have older hardware, low memory, slow CPU... all of these things will slow it down, so animation is not good on a low-end system.

If you were using Xubuntu for some reason other than old hardware, then it's probably just that Xubuntu can be expected to run a little faster on good hardware because it's intended to be used on low-end systems.

---

### Post by mharrison on 2009-07-05
> **Nevart said:**
> 
Since you've upgraded from Xubuntu, you probably have older hardware, low memory, slow CPU... all of these things will slow it down, so animation is not good on a low-end system.

If you were using Xubuntu for some reason other than old hardware, then it's probably just that Xubuntu can be expected to run a little faster on good hardware because it's intended to be used on low-end systems.


Actually, I have an AM2 64bit Dual-Core, 4 gigs of Ram, and a NVidia GeForce 8400, and I didn't upgrade from Xubuntu, I actually did a fresh install of Xubuntu to try it out, and then decided to go back to Ubuntu.  This is my main machine, but I do not keep data on it, so I have been playing with Kubuntu, Ubuntu, and Xubuntu to see which I like better.

I know that Xubuntu will run better on good hardware, I just thought there was a reason on Ubuntu that it took so long to close a window.

I did disable animations from Compiz Settings, and everything closes faster now except videos, but the more I am testing, it might just be Totem Movie Player.

Edit:
I went to the display settings and turned off all visual effects and video's close quicker now.  Not sure I like having all effects turned off, but I guess it's a small trade-off to have no delay when closing programs down.

---

