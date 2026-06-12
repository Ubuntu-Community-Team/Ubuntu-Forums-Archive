---
title: "screen slow to update menus,  then leaves defects or artifacts behind"
date: 2011-01-25
forum: General Help
---

### Post by sdowney717 on 2011-01-25
second time since forum seemed to eat the first post

anyway, sometimes screen leaves defect behind when menu selected.
when it does this, it is extremely slow to pull up the menu

---

### Post by Bucky Ball on 2011-01-25
Silly question, but you have the correct video driver loaded for your graphics?

---

### Post by sdowney717 on 2011-01-25
yes, i am running nvidia driver on a 9600 with MM ubuntu

---

### Post by sdowney717 on 2011-01-25
[http://www.cubicvr.org/CubicVR.js/LightingTest1.html](http://www.cubicvr.org/CubicVR.js/LightingTest1.html)

I can even do webgl on chrome

/opt/google/chrome/google-chrome %U --enable-webgl


just the strange menu issues

---

### Post by abickerton on 2011-02-26
I have the same issue running Maverick x64 and using the radeon driver with my Radeon 9600 pro.

I can't find a bug report for it though and It's tricky to reproduce reliably.

[https://bugs.launchpad.net/ubuntu/+bug/725782](https://bugs.launchpad.net/ubuntu/+bug/725782)

---

### Post by Bucky Ball on 2011-02-27
> **abickerton said:**
> I have the same issue running Maverick x64 and using the radeon driver with my Radeon 9600 pro.

I can't find a bug report for it though and It's tricky to reproduce reliably.

[https://bugs.launchpad.net/ubuntu/+bug/725782](https://bugs.launchpad.net/ubuntu/+bug/725782)

Much better to post a new thread outlining your issues. 

This one's old and your well buried here with a thread title that doesn't really cover your issue ... post a link to the new one here and we'll see what we can do ... ;)

---

### Post by sdowney717 on 2011-02-27
huh?
anyway It is still an issue, but not as much as before.

---

### Post by jelabarre on 2011-03-14
I get the exact same problem, but with a 32-bit install, and on an Intel GM965/GL960 display adapter (T61 thinkpad).  Have seen the same thing happen with an ATI Mobility Fire GL T2 (Thinkpad T42p).  Have all Compiz packages *uninstalled & purged* on both, so not a Compiz issue.
 
Now have also seen the same on Mint 10 (based on Ubuntu 10.10).  The only way I have found to clear the artifacts is to find the menu that drew the object in the first place and re-open it so it redraws the item CORRECTLY the second time around.  Problem is, sometimes that will cause a *different* menu item to fail in it's redraw :confused:

---

### Post by sdowney717 on 2011-03-15
I am trying something new. I created a new user and logged in.
So far laggy menus are gone.
I will post back as I keep on keeping on.

you will have to goto user and groups and basically make your new user an admin with all privileges.

---

