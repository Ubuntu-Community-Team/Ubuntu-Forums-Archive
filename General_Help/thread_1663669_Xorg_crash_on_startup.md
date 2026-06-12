---
title: "Xorg crash on startup?"
date: 2011-01-09
forum: General Help
---

### Post by chillyperson23 on 2011-01-09
Today, everything was working fine until I started an upgrade.   After the upgrade finished,  my bluetooth keyboard stopped working, so i connected another keyboard and CTRL ALT Backspaced.   The screen turned off, then turned on, but blank.   The login screen didn't show, and i couldn't even switch to TTYl.   The only way i got anything to work was renaming /etc/gdm and rebooting.  then i had to switch to TTY while plymouth was running. 

Then i logged as root and ran startx, and it froze, once again.   

If i try to boot into recovery,  it doesn't work either.  :confused:  

Any help?  :E

---

### Post by Bucky Ball on 2011-01-09
Upgrade? From what to what?

What happens when you boot into the recovery? Can you get to the recovery options? If so, what happens if you drop into 'Failsafe x'?

---

### Post by Synapsi on 2011-01-09
I have had this same problem as well.  Pressed Ctrl + Alt + F11 after updating (sudo apt-get update and sudo apt-get upgrade) from terminal.  Now I am stuck in TTY1 just like he is. 

Nothing is working

sudo startx = not working
uninstalling and reinstalling ubuntu-desktop = not working
other stuff i read on the forum = not working.

---

### Post by Bucky Ball on 2011-01-09
Confused. 

chiilyperson: Upgrading to a new release, 10.04 LTS for instance?

synapsi: Not sure if this is the same problem yet. You should probably start a new thread if OP was *upgrading* as you appear to be having problems with *updating*.

Not the same issue and confusing attempting to fix two separate issues on the same thread.  ;)

---

