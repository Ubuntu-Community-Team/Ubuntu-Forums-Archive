---
title: "X server problem?"
date: 2006-03-11
forum: General Help
---

### Post by ILikeLinux on 2006-03-11
Hi, 

I have perfectly working breezy version except for one problem. 
If in the middle of my session, I do a CTRL-ALT-F1, I get the console
and I can login, run commands etc. But when I want to get back
to my GUI session, by doing CTRL-ALT-F7, I just get a screen, 
without any graphics. In fact, I have tested this : I just kept
one terminal open, in my gui (X) session, I also copied the text
"**ping 192.168.0.1**"

Then, I did CTRL-ALT-F1 and logged on to console, did a ps,
to see the processes those are running. Then, I did CTRL-ALT-F7,
In that I pasted the text by CTRL-V and hit the enter key, (remember
that I am not seeing anything on the screen, the screen is more 
or less black), then I do again CTRL-ALT-F1 and again a ps. This
time it shows that the ping is running, earlier there was no ping
running, which means things are working, as they should, only I 
don't get to see anything in the screen. 

The same thing happens, if I logout. After logging out I don't see
the login screen back. But I can type my user name, password
and can login. I can verify this by seeing the processes running, 
from the console. I posted this in the thread

[http://www.ubuntuforums.org/showthread.php?t=140490](http://www.ubuntuforums.org/showthread.php?t=140490)

and tried things like restarting gdm or installing kdm etc. None
helped. Only way, is to reboot the machine from the console. 

Help please!!!

---

### Post by youbaji on 2006-03-11
you can kill the X by pressing "ALT+CTRL+Backspace" after you press "ALT+CTRL+F7".  Then X will restart over again.

---

### Post by ILikeLinux on 2006-03-12
I did try that, it seems that the login screen comes, I can verify that
from the processes running, from the console. But screen remains 
black as usual.

---

