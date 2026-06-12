---
title: "View all Ubuntu screens at 640x480 ??"
date: 2010-09-29
forum: General Help
---

### Post by thetao on 2010-09-29
I am currently stuck on a non-PnP monitor that doesn't appear to do  better than 800x600, and am surprised how difficult it's been to view  every Ubuntu screen normally.  I am using a very stock Ubuntu 10.04 LTS  with stock video drivers and no special themes or splash screens.  I can  get Gnome at 800x600 at 56 Hz (doesn't seem to like 60 Hz), and the  Grub boot menu always renders fine.  But making all other video render  legibly has been an exercise in frustration:

1) Startup-Manager does nothing for video size.
2) No edits I make to the /etc/default/grub file (yes, I am also running  update-grub) has made any difference, except cause Ubuntu to hardly  boot at all (with a "Ubuntu is now running in low graphics mode" error)
3) And the other half dozen tutorials and blogs I've read have also done nothing

The only suggestion that's helped is [http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/](http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/),  for rendering the graphical login screen properly.  I still have no  idea how to make the Ubuntu logo startup and shutdown screens render  properly (at this point I want nothing more than 640x480), and to make  the six console screens (i.e. Ctrl + Alt + F1) and any other text  screens usable.

I did notice that if I change the GRUB_CMDLINE_LINUX_DEFAULT argument in  the  /etc/default/grub file to "", then I see a readable screen of text  as Ubuntu runs its startup scripts.  But later text screens (like the  six consoles) become garbled.

In my web searches, [http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html) seems to suggest this is some kind of bug, a problem with Grub not being able to communicate with the kernel??  If  so, I assume somebody is working to fix it?  For a distribution like  Ubuntu that strives for user-friendliness, this really shouldn't be such  a problem. :(

Thanks for any suggestions!

---

### Post by thetao on 2010-10-02
Anybody?  Maybe I should take this to IRC....

---

### Post by TBABill on 2010-10-02
Have you attempted to see if a proprietary driver is available for your video card? System>Administration>Hardware (or additional hardware in 10.10).

---

### Post by thetao on 2010-10-03
I could try that, but I'm unclear why that would be the problem.  I can switch between 640x480 and 800x600 at will when within the Gnome desktop.  It's only when something else is displayed that the video rules seem to change.

---

### Post by JOHNNYG713 on 2010-10-03
I have had this happen, and found That if I switched monitors from my ESA to my DELL I had no problem, I know not much help, but if you have access to an other monitor give it a try!

---

### Post by thetao on 2010-10-03
If I had access to another monitor, I wouldn't have noticed this bug (?) in the first place. :(  Thanks nonetheless.

---

### Post by jamarsa on 2010-10-29
Ah, yes, I had this same struggle when I was trying to adapt ubuntu to start as a Point of Sale with a small 9" screen. Same results here; text screens change to a double (and tiny) font once init (upstart?) fires on.
Tried for days.

Edit: [[COLOR="Red"]This[/COLOR]]("http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/") seems to do the trick. :P

---

