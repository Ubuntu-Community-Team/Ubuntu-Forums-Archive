---
title: "Can't log in ubuntu 10.04"
date: 2010-09-23
forum: General Help
---

### Post by engine8470 on 2010-09-23
I updated the system and after rebooting, i was not able to get past login screen. When i enter my password, screen goes black for 3 seconds and then i am back to the login screen...
What is happening?
Thanks in advance...

---

### Post by bryanfblareunion on 2010-09-23
At login screen, press CTRL+ALT+F1. That takes you to a terminal version of ubuntu. See if you can log in with that.

---

### Post by engine8470 on 2010-09-23
Thanks for the reply.
Yes I can. What do you suggest??

---

### Post by engine8470 on 2010-09-27
nobody? please help guys... i've searched and i can't find a solution.

---

### Post by hrickh on 2010-09-27
Sounds like you updated your kernel, but not your graphics driver.

What graphics card are you using?

R.
==

---

### Post by engine8470 on 2010-09-28
thanks for your reply.
i use nvidia 260gtx. i had updated  the drives one day or two i think, before this happened. if this is the case what do i have to do?

---

### Post by hrickh on 2010-09-28
> **engine8470 said:**
> thanks for your reply.
i use nvidia 260gtx. i had updated  the drives one day or two i think, before this happened. if this is the case what do i have to do?
You need to go back and re=update your nVidia drivers. Any time you update your kernel, you need to update your video drivers t the same time.

R.
==

---

### Post by engine8470 on 2010-09-28
I removed the old ones and the installed the currrent ones with
```
sudo apt-get install nvidia-current
```
and it still does the same thing...
What has happened???

---

### Post by engine8470 on 2010-09-28
Forgot to mention this is also happening in Failsafe gnome.

---

### Post by tolputt on 2011-01-10
Also having the same problem, although have not updated anything since last power down.

It doesn't seem to a graphical problem as graphics are fine, on the login screen. 

Am able to login through Ctrl+Alt+F1 too..

If anyone has any ideas, it would be greatly appreciated.

---

