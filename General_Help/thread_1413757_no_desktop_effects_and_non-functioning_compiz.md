---
title: "no desktop effects and non-functioning compiz"
date: 2010-02-22
forum: General Help
---

### Post by Shifat on 2010-02-22
So I was messing around on my laptop this morning and I noticed that my desktop effects were turned off. So i decided to turn them on but as soon as i pressed the "normal" option a pop up opens up and says "searching for drivers" then the screen flickers and finally it tells me "desktop effects cannot be enabled". Also my compizconfig wasn't functioning:(. for exmaple: I turn on wobble windows and nothing happens. No wobble windows.

Please anybody that knows how to fix this issue help me out! I'm sort of still an ubuntu newbie so please try to make the instructions simple :P

Thanks

Shifty

---

### Post by drpjkurian on 2010-02-22
I think that your driver has been disabled

---

### Post by theozzlives on 2010-02-22
> **Shifat said:**
> So I was messing around on my laptop this morning and I noticed that my desktop effects were turned off. So i decided to turn them on but as soon as i pressed the "normal" option a pop up opens up and says "searching for drivers" then the screen flickers and finally it tells me "desktop effects cannot be enabled". Also my compizconfig wasn't functioning:(. for exmaple: I turn on wobble windows and nothing happens. No wobble windows.

Please anybody that knows how to fix this issue help me out! I'm sort of still an ubuntu newbie so please try to make the instructions simple :P

Thanks

Shifty

What kinda video you got?

---

### Post by thecliff on 2010-02-23
Agreed - it is highly likely that you do not have the correct video drivers installed.  It has generally been my experience that the open source ATI driver (radeon) will not allow the best desktop effects but the proprietary ATI driver will allow you to use the desktop effects and compiz.  

What make/model video card do you have?  Where drivers found when the machine searched for them?

---

### Post by Jeromin on 2010-02-23
Hello all, 

I'm new to this forum and have recently installed 9.10. I am getting the same desktop effects could not be enabled message. I have a Dell Optiplex gx 620, 2 gb ram and ATI 4350 GC. I activated proprietary drivers.

after running " lspci | grep VGA"
I got:
 "ATI Technologies Inc RV710 [Radeon HD 4350]"

Any help appreciated

Jeromin

---

### Post by Shifat on 2010-02-23
I dont know what graphics card i got but all i know is that its integrated and its intel

---

### Post by arcanewulf on 2010-02-23
integrated graphics cards are terrible, especially intel, whose integrated graphics were developed with the intentions of providing basic users with the means to use the internet, and edit word documents.

Likely, you don't have the graphics power for the effects you're trying to use.

---

