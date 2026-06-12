---
title: "minimise,maximise,close buttons in Unity"
date: 2011-06-17
forum: General Help
---

### Post by niko-nojo on 2011-06-17
Hi all,
Do anyone know how to get the minimise,maximise,close buttons on a menu in Unity Ubuntu 11.04 ?

Thanks.

---

### Post by westie457 on 2011-06-17
> **niko-nojo said:**
> Hi all,
Do anyone know how to get the minimise,maximise,close buttons on a menu in Unity Ubuntu 11.04 ?

Thanks.

Hi they should appear in the left side of the bar at the top of the screen unless a program is running in full-screen mode. The only suggestions I have are 

For a Browser window  eg. Chromium Web Browser  press F11 to exit full-screen mode.

For other programs try the Esc button.

If these do not work for you come back here and someone more knowledgeable than me should have some more suggestion for you.

---

### Post by niko-nojo on 2011-06-17
For example - I've opened a Terminal window and this is what I see. I wonder is it theme related. I'm a little baffled. See attached screenshot. I see the buttons only when the window is maximised.

---

### Post by westie457 on 2011-06-17
That is strange however I do not have the answer for you right now. I'm sure there is some simple line of code to input in a terminal to reset everything to default.

This has already reached the current limit of my knowledge.


Does anyone have the answer please

---

### Post by gjonatha on 2011-06-17
How did this problem start?

 Try in terminal: unity --reset

 It should reset unity settings to default

Hope it helps

---

### Post by Joe- on 2011-06-17
Open terminal type gconf-editor then select apps>metacity>general and add close,minimize,maximize to the button layout. See oist below for picture:

---

### Post by Joe- on 2011-06-17
Here's the picture:

---

### Post by niko-nojo on 2011-06-17
That layout is already there. Its been like this since I upgraded to 11.04

Unity --reset does not work either.

---

