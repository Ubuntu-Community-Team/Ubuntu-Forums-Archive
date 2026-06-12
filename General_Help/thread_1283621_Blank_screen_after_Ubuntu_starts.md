---
title: "Blank screen after Ubuntu starts"
date: 2009-10-05
forum: General Help
---

### Post by dkknight593 on 2009-10-05
I get a blank screen after Ubuntu starts up.

I am running Ubuntu 9.04.  using flgrx driver for my ATI card.

I didn't have problem prior.

---

### Post by lidex on 2009-10-06
What changes did you make prior to your problem?

---

### Post by dkknight593 on 2009-10-06
I have Gnome bar and on it Pidgin uses the same status area as the logoff/shutdown button.

I was trying to bring up Pidgin to make sure I was properly logged in.  I clicked guest or something on the drop down menu and boom the screen blanked.

Since then Ive been in this wierd mode were Ubuntu is running but I can't see anything.  It looks like screen lock without the screen saver running.

It might be a mode which my card does not support.  The Xorg.conf file is pretty bare except for the driver set as flgrx.  I was also looking for the flgrx.conf file to see if that might help.

I might try removing the flgrx and go with just ati or vesa.  Last resort trash and reinstall Ubuntu.

---

### Post by lidex on 2009-10-06
Is this a laptop? Give us some specs, if you don't mind. Are you able to access desktop?

---

### Post by dkknight593 on 2009-10-07
Its A Dell Inspiron 530 desktop with a Core 2 Duo and 2GB RAM .
Using a ATI Radeon 3650 HD video card with the flgrx driver.
I have dual boot system with Windows Vista on another partition.
Home, Boot, OS, and Swap have their own partitions.

I have been using this setup for over a year now until now.

I am forced to work on Vista for now...  What a pain.

---

### Post by dkknight593 on 2009-10-07
I've played around with the Xorg.conf file to see if that would help.  No sucess if I use any other driver other than fglrx I get a garbled frozen screen (tried vesa and ati).  Reconfiguring Xorg does not work either.

Looks like I'll have to reinstall.  Unless anyone has any suggestions.

---

### Post by cdbitesky on 2009-10-07
I have the same exact graphics card dk and whenever i have had any drivers installed, but the ati propriety i have had screen issues and freezes. How long have you had flgrx drivers installed?

---

### Post by dkknight593 on 2009-10-08
About a year now.  Never had problems with the open source driver before I installed the fglrx driver.  When I run from live CD I have no problems.

The fglrx drivers cause a conflict with open source drivers.  In the Faq it says to uninstall them first.

My Xorg.conf file really had only two settings Device Driver set to fglrx and load glx in the module section.  rest is just generic with no settings.  It seems like the Xorg never configured properly, but the computer was working with those settings before.

---

### Post by dkknight593 on 2009-10-16
This issue seems to have resolved on it's own for some unknown reason.  

When I tried to boot up my puppy linux to get take a look at files.  I left the room and turned off the monitor.  Came back and switched on the monitor.  Same blank screen same with Vista this time.  Messed around with the monitor cable and Ubuntu came back up.  

Maybee intermitent connection?  Maybee it thought the monitor was disconnected like in laptop mode or something.

All's well as ends well.

---

