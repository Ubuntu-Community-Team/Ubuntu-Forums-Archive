---
title: "avant window navigator"
date: 2011-05-02
forum: General Help
---

### Post by irakla7777777 on 2011-05-02
i have installed avant window navigator . 
when start skype and close it , disappared .
skype still running as background but noo icon in awn.

how to solve it ?

---

### Post by micael3000 on 2011-05-02
Try executing "compiz --replace", it will reload the panel and hopefully it will show up skype.

---

### Post by irakla7777777 on 2011-05-02
it was not helpful .
i have a very big problem  on compiz .

see my post 
[http://ubuntuforums.org/showthread.php?t=1743383](http://ubuntuforums.org/showthread.php?t=1743383)

i cannot fix it

---

### Post by micael3000 on 2011-05-02
I gave up on desktop cube because of it's incompatibility... My system is still completely messed up but... You could do the same. :s

This new Ubuntu is usable but they haven't improved it enough for an official release (like 11.04) -- in my opinion --. I may get used to it but I think we will have this General Help forum completely full on the middle time.

In fact, ubuntu is pretty powerful and stable but they aren't helping X-users recently by improving its visual resources :(

---

### Post by moonbeam on 2011-05-02
See [https://bugs.launchpad.net/awn/+bug/218603](https://bugs.launchpad.net/awn/+bug/218603) for a discussion about a related issue with Skype.  

The taskmanager does not show any task when skype is minimized to the notification area because it has no window opened.  This behaviour is present for all applications that allow a minimize to the notification area.  

There are two possible ways to get the desired behaviour.

1) If the application allows only one instance then just create a launcher for it - normally if an attempt to launch a new instance occurs and the app is in the notification area then it will restore it's window.

2) Configure the app to _not_ minimize to the notification area.

---

### Post by Vaphell on 2011-05-02
do you have indicator applet enabled in your awn? It should show all system tray items. I had the same issue with pidgin but i can restore it thanks to that (also permanent launcher helps because it does what moonbeam said in 1.).

---

### Post by irakla7777777 on 2011-05-02
i have enabled indicator applet.
but when close skype whit X button , its icon disappeared.

did you try this on skype ?

---

### Post by irakla7777777 on 2011-05-03
i am using  avant window navigator , and have problem on skype.
when i type close button it  disappear and still running as background. 

Anybody knows a solution?

---

