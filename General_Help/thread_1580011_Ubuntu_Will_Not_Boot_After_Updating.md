---
title: "Ubuntu Will Not Boot After Updating"
date: 2010-09-22
forum: General Help
---

### Post by SignatureSeriesOwner on 2010-09-22
Hi all,

I just installed ~ 100MB worth of updates to Ubuntu, and excluded about 150MB to do at a later date.  After installing them, it told me I needed to reboot.

So, I clicked the button, and rebooted the computer.  Now Ubuntu will not boot up.  I'll select launch Ubuntu, and a little blinking period will show up in the top corner of the screen for around 10 seconds, then a message will flash across the top of the screen saying "cannot process..." or something,  then a quick green flash, then black silence.  My screen stays lit, but the screen is just black.  The HD light goes out shortly after.  Booting in recovery mode doesn't seem to do much either.

Have any of you ran across this?  Did I manage to kill Ubuntu?

---

### Post by clhsharky on 2010-09-22
SignatureSeriesOwner

Was this a fresh install of Lucid, or upgrade to Maverick?
What video chip?

Sharky

---

### Post by Billsey on 2010-09-22
I am having that problem, too, since the latest update of 9.10. I am using an Intel motherboard with integrated graphics and a 1.8GHz Pentium4 with 1.25 GB RAM. In recovery mode, I can see that it gets to the point of starting the ntd (or ntp) something or other, then drops to a shell prompt from which I can log in, but that doesn't really help, since I NEED the graphical environment to get anything done. :-/

Right not I am booted up from a 10.04 LiveCD, but I'd really rather not have to go through the trouble of finding and installing all the apps I use YET AGAIN becuase the LiveCD does not recognize and simply update an existing install.

---

### Post by SignatureSeriesOwner on 2010-09-22
It is a fresh install,  I was just getting around to tinkering/updating it.

Ubuntu 10.04.

nVidia GeForce 6100 graphics card.



EDIT:  the error is actually "Error probing smb2" if that helps.  It seems that even if people get it, the OS is still able to boot.  Not so in my case.

---

