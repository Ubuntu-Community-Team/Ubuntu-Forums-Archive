---
title: "Need way of making the desktop read-only"
date: 2010-05-25
forum: General Help
---

### Post by ectospasm on 2010-05-25
I have installed Ubuntu 9.10 for my ninety-two year-old grandfather, and he loves it.  The only problem is, he clicks on everything on his GNOME desktop, and manages to delete everything, including menus, icons, etc.  The people he lives with aren't skilled enough to fix it, and I live a good eight hours away.  I have remote capabilities with NX, but that requires them to initiate a connection to my workstation here, which is more painful than I thought it would be.

I need a way of locking down the desktop, so it's read-only, so he can't make the changes he seems to keep making. I figure I could make the .gnome directory read-only, but I don't know if that would affect the normal operation.  Does anyone have any ideas?

---

### Post by Shrav on 2010-05-25
> **ectospasm said:**
> I have installed Ubuntu 9.10 for my ninety-two year-old grandfather, and he loves it.  The only problem is, he clicks on everything on his GNOME desktop, and manages to delete everything, including menus, icons, etc.  The people he lives with aren't skilled enough to fix it, and I live a good eight hours away.  I have remote capabilities with NX, but that requires them to initiate a connection to my workstation here, which is more painful than I thought it would be.

I need a way of locking down the desktop, so it's read-only, so he can't make the changes he seems to keep making. I figure I could make the .gnome directory read-only, but I don't know if that would affect the normal operation.  Does anyone have any ideas?

Can't help you with that but what about making a copy of his home directory and creating a script that over writes his with the copy? Don't know if that is possible but if it is when you get the panic phone call, just tell him to reboot and it would be back to as you set it up. 
Maybe someone who is adept in scripting can chime in here.

Just a thought!

---

### Post by ectospasm on 2010-05-26
I found this site which may allow me to set up what I need to with it:

[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

It's for a quite old version of Ubuntu, but the fundamentals should still be valid.  I'm not looking forward to doing this remotely, but hey, it's a challenge!

---

### Post by mister_p_1998 on 2010-05-26
I did this for my five year old son, I just opened a terminal, sudo nautilus, and made all the icons shortcuts read only.
that way, he can move things about but not delete anything. I never thought about locking down the applications menu, but he has everything he needs on the desktop, I dont think he ever goes there, Ive had no problems in over a year.
Steve

---

