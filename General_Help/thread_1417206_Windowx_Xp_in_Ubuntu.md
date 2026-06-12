---
title: "Windowx Xp in Ubuntu"
date: 2010-02-27
forum: General Help
---

### Post by CatchItBaby on 2010-02-27
Is it possible to run Window XP in ubuntu ?

If yes plz refer me any guide / Tutorial

Thanks

---

### Post by d3v1150m471c on 2010-02-27
use virtual box

[Tutorial]("http://www.youtube.com/watch?v=ch8X86R6d-g&feature=player_embedded")

I didn't have to do anything with the user groups like in the video. Get a copy of xp, launch virtualbox, create a new system, tell it to boot from the .iso somewhere on your computer and install it. Look into installing the guest additions so you can ctrl+f to fullscreen virtualbox.

---

### Post by talhaguy on 2010-02-27
You could also try Wine, which lets you run windows programs. Not all programs work through wine but some do. For example, I am able to run MS Word 2003.

---

### Post by Vaphell on 2010-02-27
in general if you need apps that use a lot of raw power, a lot of 3d etc (games) you should try wine. If you don't mind the overhead of virtual machine and need some 'ordinary' stuff, running it from VirtualBox will be less hassle - after all the app will think it works in a true windows environment so it should be 100% compatible.

---

### Post by Mark Phelps on 2010-02-27
Having first-hand experience with Wine (mostly negative, by the way) it's only really useful for a very limited number of Windows apps, and even then, for specific versions of those apps.

You should check the WineHQ Application Compatibility website for the specific apps and versions you want to run before you install Wine.  Some stuff works great, other stuff OK, a  lot of stuff -- not at all.

As a more general purpose approach, VirtualBox gives you an XP-in-Ubuntu solution, but from what I've read (don't use it myself), it's not useful for 3D gaming due to the inability to utilize hardware acceleration on the video card/chip.

---

