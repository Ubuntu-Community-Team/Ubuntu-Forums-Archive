---
title: "why does this error show"
date: 2012-03-08
forum: General Help
---

### Post by nataliafoster26 on 2012-03-08
i istall freeglut3-dev
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
i uninstall it and install it back and same error
thanks

---

### Post by swright007 on 2012-03-08
Two things to check.. first you need to check to see whether your 3D drivers for your card were installed or not.  Second, go into your video settings and make sure, if you know they are installed, that they are turned on.

---

### Post by swright007 on 2012-03-08
In most situations NVidia works really well with Linux (sometimes, but not always needing extra drivers), ATI, however, requires special drivers and is a bit more picky.  Please check to see what video platform you are using ..

---

### Post by nataliafoster26 on 2012-03-08
sorry for my ignorance but how would you check all those stuff 
im new to this 
thanks

---

### Post by swright007 on 2012-03-09
[http://www.ehow.com/how_4742561_which-graphics-card-have-ubuntu.html]("http://www.ehow.com/how_4742561_which-graphics-card-have-ubuntu.html")

that will help you find out what card you have 

I believe you open a terminal and issue :  lspci
(that is LSPCI) in lower case it is hard to tell .... when it spits out it's readout just look for your video card type.

---

### Post by swright007 on 2012-03-09
I'm sorry, there are folks that have used the system longer than others.  I wasn't trying to be confusing.     I will help as best I can.  The info you answer back with will help other folks here see what you are working with. Also, it might help to know which version of Ubuntu you are running.

---

