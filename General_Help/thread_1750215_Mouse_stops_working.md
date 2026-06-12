---
title: "Mouse stops working"
date: 2011-05-05
forum: General Help
---

### Post by yoda3616 on 2011-05-05
I have recently upgrateded to 11.04 from 10.10.  I am not using the Unity feature because my hardware does not support it.  I have searched the forums for this problem and it seems that no one else is having the same problem.  Basically what happens is that my mouse (wireless USB) stops working after a while.  And when I say it stops working, that might be a bit misleading.  After a while I can no longer click anything in the workspace but I can still use the mouse to change workspaces.  Nothing else works though (menus, panels, etc).  I am able to navigate and use the computer with the keyboard.  This mainly happens when I have a lot of simultaneous tasks running.  Is there a setting somewhere that I am missing?  Is this something that other users have experienced?  I'd like to continue with 11.04, but if I can't get this figured out, I'm afraid I'm going to have to roll back to 10.10.  Any suggestions are appreciated.  Please keep in mind that I am a complete noob.  
 
Thanks.

---

### Post by danielphillips on 2011-05-07
I can confirm this also happens to me. Upgraded to 11.04 two days ago. Kubuntu. Mouse loses ability to click on any widgets except main widgets like "K" button. Can still raise windows by clicking. This has happened twice on resume, once immediately after login on reboot. Can recover by "sudo killall Xorg" and re-login.

---

### Post by danielphillips on 2011-05-09
It seems to be a USB problem associated with resuming from suspend to memory. I can restore mouse click functionality by disconnecting my USB mouse and reconnecting. Still a major bug but at least I no longer need to log out to restore functionality.

---

