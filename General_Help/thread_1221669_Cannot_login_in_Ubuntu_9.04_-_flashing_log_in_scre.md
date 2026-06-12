---
title: "Cannot login in Ubuntu 9.04 - flashing log in screen and desktop"
date: 2009-07-24
forum: General Help
---

### Post by jfagh on 2009-07-24
I have been using 9.04 for several months, no problems. Last night I installed some automatic updates (one of them was a Firefox update) When I restarted my laptop (Sony VAIO TZ), the login screen kept flashing and the mouse would reset to the middle of the screen after every flash. 

I spent the whole day trying to fix this but no luck :( I re-installed gdm and ubuntu-desktop but that didn't work. I tried to bypass the login screen by setting autologin on but it gives the same results on the desktop (a flashing screen and you can't do anything except CTR+ALT+F1/DEL)

Does anybody have a solution? If not, is there a way to re-install ubuntu 9.04 from the terminal, without loosing my data?
Thank you

---

### Post by wking on 2009-07-31
Hi I also have a TZ and I think that I have been having the same problem as you for a while now. I think that I have just found a solution - I am not an expert but I believe it is in the initialisation of the graphics screen it is getting reset. (Mine goes back to login all the time)

Now this is not a way to fix it but a hack to possibly get around it.

What I do is put in the username and then the password and immediately go to CTRL-ALT-F1 to another console screen and the actual machine will log (music plays and all) on the other hidden screen. When it has settled down - then I will type the CTRL-ALT-F7 screen and then my desktop is waiting for me.

(I am using synergy and I am not sure if this is causing problems - it has worked fine for 8.04, 8.10 previusly however)

So it is not a fix but a workaround - hope that helps

---

