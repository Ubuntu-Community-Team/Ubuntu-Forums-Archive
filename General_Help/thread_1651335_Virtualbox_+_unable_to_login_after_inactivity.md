---
title: "Virtualbox + unable to login after inactivity"
date: 2010-12-23
forum: General Help
---

### Post by catnip_X07 on 2010-12-23
Running Ubuntu 10.10 within virtualbox on ubuntu 9.10.  Noticed an odd item that was once an peculiar and has now become an annoyance.

If I leave my computer for, say 5 minutes, and I bring virtualbox back up, i am presented with a login screen.  However, i can't login as my keyboard does not work.  Mouse works fine.  Can't login, so I have to close out.  

I looked at my power management settings within 10.10 and everything is off.  no power saving.  Ubuntu 9.10 has power management, but these do not appear to affect virtualbox.  I have a 15 minute monitor turnoff, with disks running until 2 hours.  If I leave for 5 minutes, monitor is on, but Ubuntu 10.10 within virtualbox wants a login.  

How do I correct this?

---

### Post by catnip_X07 on 2010-12-23
I found a quick fix to this, but isn't something I want to keep doing.  I have to go to devices, select my keyboard from the USB selection, and then I'm able to use my keyboard to login.  However, my keyboard will no longer work outside virtualbox, unless I deselect it from devices.

There has to be something easier, or more permanent, than this.

---

### Post by Verbeck on 2010-12-23
to disable the lock screen, have a look at the screen saver preferences

---

