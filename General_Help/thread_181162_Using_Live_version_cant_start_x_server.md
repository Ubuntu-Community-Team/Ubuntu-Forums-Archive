---
title: "Using Live version cant start x server"
date: 2006-05-23
forum: General Help
---

### Post by knewmocker on 2006-05-23
I am very new to using linux altogether. Actualy this is my first time. I wasnted to try it out with the live version first to see what it would be like and everytime I try to boot it up I get the error message "Failed to start X server (your Graphical Interface). It is likely that it is not set up correctly." I havent the fogiest on how I can set up my Graphical Interface. Can anyone help me?

---

### Post by ispmarin on 2006-05-23
This is the live cd, right? Can you post the exact error message that appears after the failure?

---

### Post by knewmocker on 2006-05-23
I had. It comes to a blue screen saying "Failed to start the X server (your Graphical Interface). It is likely that it is not setup correctly" Then it askes if I want to view the x server error log and has a yes and no at the bottom to choose from but before I can it gose to a prompt and there is nothing I can do by that point.

---

### Post by ispmarin on 2006-05-23
You can try to do this: when the X server hangs, try to go to another terminal pressing CRTL+ALT+F1. You should get a terminal window, log in an then tries to do startx. If the computer hangs, woo, this is new, because this sometimes happened in my desktop, but I was able to disable the X interface and boot again. Well, you can search for a option on the livecd boot to do not got the X up. I really don't know how to do it... ;-)

---

### Post by r4ik on 2006-05-23
Talking about fogg haven't got a clue if this will work on a live-cd.

sudo dpkg-reconfigure xserver-xorg     enter,

just follow the defaults until you get to youre grapics card section select "nv" for Nvidia or "vesa" (ATI)

continue and finish with,

sudo /etc/init.d/gdm stop        enter
sudo /etc/init.d/gdm start        enter

Let me know please.


Good luck !

---

### Post by knewmocker on 2006-05-23
I felt realy good about that one did everything you said and still would not startx.I think it is funny how they use the live cd to protrait how the real thing will be and I am starting to think all it will be is a head ach :|

---

### Post by r4ik on 2006-05-23
I am sorry it did not work i think i wont be able to help you much further on this one thanks for the reply.
Anybody else who can help  perhaps ?

---

### Post by Metal03 on 2006-05-23
I have the same problem...  Correct me if I'm wrong, but I'm pretty sure you have a fairly recent graphic card.

I have a EN7900GT and apparently the "nv" configuration from xserver does not work with such a recent card...  is there a way with the LiveCD to update the Nvidia database so it supports these cards?

---

