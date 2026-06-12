---
title: "Weird mouse behaviour"
date: 2010-05-19
forum: General Help
---

### Post by Smart Viking on 2010-05-19
Hi all, i just installed 10.04 on my dell latitude 5400. But something is wrong with my mouse!

The mouse behaves ok when i do not have any programs opened, but as soon as i open a program it wont respond, i can move it and all but i can't click with it at all, it happens with both the thouchpad and a wired mouse. It was also like that in the live cd, i had to install ubuntu with my keyboard. Because my keyboard works perfectly.

I have not updated ubuntu yet, i use a beta version.

Thanks! :)

PS: It is a little important since it is my school laptop.  :rolleyes:

---

### Post by Smart Viking on 2010-05-19
Ok i plugged in ethernet and tried to update the system. 

And then when i think i was trying to enable the updates from the update manager, the screen goes grey without nothing happens(where i should write my password) and then it says this:

> 
[B]Could not grab your mouse.

[/B]A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.

Try againWhat does this mean? I must admit that the bios have a password, and i do not know it. Maybe that have something to do with it?

---

### Post by Smart Viking on 2010-05-20
Hi all. I have those problems i have found out in Ubuntu 10.04, ubuntu 9.10 **and** PCLinuxOS. So i have no idea what it is. However, when i log in as root in PCLinuxOS, the mouse is working perfectly! I am glad i found a way, however i don't think it is good to be logged in as root all the time, but thats what i got to do...

If someone have any idea why i have this problem please post. :)

---

### Post by sashby on 2010-07-06
Here's something you can try.  This assumes the underlying problem is  actually with your settings that affect how your system handles window  focus and focus stealing.

I am using XFCE - if you aren't using XFCE it could still be a similar  problem, but the settings would be found  elsewhere.

1) "Applications" Menu / Settings / XFCE 4 Settings Manager
2) Uncheck "Activate focus stealing prevention"
3) Uncheck "Honor standard ICCCM focus hint"

In my case left mouse clicks weren't being detected, unless I right-clicked somewhere else (usually in the field already focused), then my next left-click would be seen properly.  A kernel update fixed the problem temporarily, but a system update last week caused the problem to reappear, along with the "COULD NOT GRAB YOUR MOUSE" error - which was totally new for me.

These settings changes solved both problems.  Good luck!

---

### Post by Smart Viking on 2010-07-23
> **sashby said:**
> Here's something you can try.  This assumes the underlying problem is  actually with your settings that affect how your system handles window  focus and focus stealing.

I am using XFCE - if you aren't using XFCE it could still be a similar  problem, but the settings would be found  elsewhere.

1) "Applications" Menu / Settings / XFCE 4 Settings Manager
2) Uncheck "Activate focus stealing prevention"
3) Uncheck "Honor standard ICCCM focus hint"

In my case left mouse clicks weren't being detected, unless I right-clicked somewhere else (usually in the field already focused), then my next left-click would be seen properly.  A kernel update fixed the problem temporarily, but a system update last week caused the problem to reappear, along with the "COULD NOT GRAB YOUR MOUSE" error - which was totally new for me.

These settings changes solved both problems.  Good luck!

Thank you, that sounds very much like the problem i am having, i'm currently using xterm since that works, i will install xubuntu and try your soluton right away. :)
EDIT: Those tips didn't help me with my problem, FYI.

---

### Post by Smart Viking on 2011-01-15
After having given up on this PC for a long time, i just now booted it up with a live CD with Ubuntu 10.10, and the mouse doesn't seem to have that behavior anymore. So if anyone have the same problem, try ubuntu 10.10, seems like there have been some changes that make it work. :)

---

