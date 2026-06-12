---
title: "symbol lookup error glwMDrawingAreaWidgetClass"
date: 2011-03-07
forum: General Help
---

### Post by LonelyStar on 2011-03-07
Hi,

I am trying to execute a program "PHANToMTest" which I got from the homepage of the manufacture of my Phantom Devicde "SensAble". The program outputs:

PHANToMTest: symbol lookup error: PHANToMTest: undefined symbol: glwMDrawingAreaWidgetClass

If I understand the google search results, I got about this, correctly, It is because libGLw is compiled without the __GLX_MOTIF defined. I tried compiling the mesa lib by hand, but got the same problem.

What can I do?

Thanks!
nathan

---

### Post by shams1363 on 2011-05-17
Hi Nathan,

I encountered exactly the same problem. Did you find any solution for that?

thanks,
Shams

---

### Post by LonelyStar on 2011-05-17
Hey,

Other than not using the test program, no. Sorry.

Do you use a Phantom with FireWire connection?
If yes, does it work with ubuntu 11.04? I have trouble with the raw1394 kernel driver and I am wondering if you have the same problem.

Greetings,
Nathan

---

### Post by shams1363 on 2011-05-19
Hi Nathan,

Unfortunately, we are very new to this topic. We started working with Phantom a couple of days ago, and have not been successful to install it correctly.

Bests,
Shams

---

### Post by shams1363 on 2011-05-23
We used openhaptic toolkit instead of the sample. 
[http://www.sensable.com/products-openhaptics-toolkit.htm](http://www.sensable.com/products-openhaptics-toolkit.htm)
It works very nice with ubuntu.

Shams

---

### Post by seyon on 2011-05-27
How did you manage to solve that problem? When i try to run PHANToMTest i got that error, even with motif support compiled on Mesa and after check for any conflicting libraries.

> **shams1363 said:**
> We used openhaptic toolkit instead of the sample. 
[http://www.sensable.com/products-openhaptics-toolkit.htm](http://www.sensable.com/products-openhaptics-toolkit.htm)
It works very nice with ubuntu.

Shams

---

### Post by seyon on 2011-05-30
I've compiled a MesaLib version 7.5.2 with --enable-motif and i've manage to run PHANToMTest successfully :)

---

### Post by LonelyStar on 2011-05-30
Cool, thanks for the tip!

---

### Post by amajewicz on 2012-06-26
Hello, 

I know this is an old thread but I'm having the same problem. I did compile Mesa 7.5.2 with --enable-motif but it still gives me the same error. Is there anything else I can check? There is mention in another post about 'conflicting libraries'?

Thanks!
Ann

---

### Post by Elfy on 2012-06-26
Closed - please start your own thread

---

