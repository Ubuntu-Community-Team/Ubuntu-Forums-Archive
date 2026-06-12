---
title: "Ubuntu 11.04 problem"
date: 2011-05-05
forum: General Help
---

### Post by Asghan on 2011-05-05
I recently installed the new 11.04 on my Viso desktop and it worked without a problem.. Downloaded, installed, cleaned up and then rebooted... That was the last I saw of my desktop.

  Once it restarted I could see the desktop background and all my icons of pictures notepads and useless crap. But everything on the side(top, side, bottom), the little side bars that hold all the icons for firefox and access all the system menus are not visable or accessable. They just dont exist. It took me three hours from going into my pictures folder and backing up to the system files to track down where the firefox program was hiding just so I can get on here and see if anyone could help me with this problem.. 

  Like I said, I cannot see or use any of the buttons to access system menus so I cannot open things like update manager or the terminal. I am sure there is some easy shortcut to do this but I am an IQ level 10 idiot when it comes to ubuntu and the linux ways...

  Any help would be appreciated, thank you.

---

### Post by spikoley on 2011-05-06
It sounds like it might be the same [bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788") I have.  A temporary work around is to use Ubuntu Classic mode.  On the log in screen click on your user name and then at the bottom change the drop down to Ubuntu Classic.  This will load Gnome instead of Unity.

Go to System> Administration> Additional Drivers and status message at the bottom.  Does it say, "This driver is activated but not currently in use"?  If it does then you have the same bug.  You will need to use classic mode until they fix the bug.

Then check what video card you have and post the results on the bug report.

```
lspci
```

---

### Post by Asghan on 2011-05-07
Thanks for the advise, I changed to Ubuntu Classic. Then it loaded fine. Just to test it I then logged out and changed it to 'Ubuntu' just to see what happened. Then it loaded perfectly. Now I can see and use everything just fine.

  Thanks again for the help. :)

---

