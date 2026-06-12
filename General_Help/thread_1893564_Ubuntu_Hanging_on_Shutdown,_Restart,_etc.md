---
title: "Ubuntu Hanging on Shutdown, Restart, etc"
date: 2011-12-10
forum: General Help
---

### Post by tomopotamus on 2011-12-10
I have an issue that hopefully can be solved painlessly!  Whenever I go to shutdown, restart or anything like that, Ubuntu "hangs"; and not on the Ubuntu splash screen like I've seen others mention.  What happens to me, is that the icons on the desktop change to the default GNOME icons, the panel and Unity launcher disappear, and everything will just sort of idle for a minute or two before the process completes itself.  (I can also right click and get the menu as well.)

This is a problem that started about a week or two ago.  When I first installed Ubuntu 11.10 on this computer, everything worked fine.

What info should I post in order to help get to the root of the problem?

Thanks in advance!

---

### Post by sum1nil on 2011-12-10
I hope I'm remembering correctly because this sounds like what happened to me once when I altered my window manager. The solution was resetting Unity by typing 'unity --reset' into a terminal.

But since I couldn't open a terminal in a normal start up, I had to hold left shift while booting to get to the grub menu. 

I choose the recovery console from the menu to boot without starting the X server then entered the 'unity --reset command. After that and a reboot, I had the normal graphical environment again.

---

### Post by tomopotamus on 2011-12-11
I don't know if that would help me because everything is normal until I choose to log out, shutdown, or something like that.  That's when everything just sort of hangs for about a minute or so before finishing the process.

Thanks though!

---

### Post by tomopotamus on 2012-01-12
I stumbled upon the fix to this problem recently by accident.  I had installed Gmail Offline in Chrome sometime back, and since I never use it, I decided to remove it from Chrome.  Right after I did that, everything went smoothly!

---

