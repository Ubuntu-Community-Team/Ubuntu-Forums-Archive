---
title: "Opengl based applications freeze when windows is selected."
date: 2009-12-29
forum: General Help
---

### Post by mbogucki on 2009-12-29
Hello All,

I've got an odd issue that I've been trying to resolve ever since I've upgraded to Karmic. 

This issue seems to occur within opengl-related apps such as glxgears and various second-life viewers.

When I go to select the opengl-related window, the application seems to freeze or halt. As soon as I select another
application such as gimp, firefox, chrome, etc, the opengl application starts running again. 

I found rather than using the mouseclick to select the window, I can use my mouse-wheel to "scroll-select" 
which seems to keep the app running, if I grab the window and move it slightly 
it seems to unfreeze as well as (re)minimize.

My particular system is running in a triple-head mode, using two Nvidia GTX260's, with Xinerama turned on.

As a quick test, I downgraded to a single display, (turning off Xinerama) and noted that the issue seems 
to disappear.

Has anyone seen anything like this?

System specs are as follows:

i7 Quad Core- 2.67 Ghz
(2) Nvidia GTX260's


X.Org X Server 1.6.4
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux motoko 2.6.31-15-generic 
Nvidia Driver: 190.53. (NOTE: I've tried 185.18-31, 158.18-36, 190.42, etc)

Thank you for your time.

--Mike

---

