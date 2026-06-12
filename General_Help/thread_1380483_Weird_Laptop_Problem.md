---
title: "Weird Laptop Problem"
date: 2010-01-13
forum: General Help
---

### Post by TwiztidChef on 2010-01-13
I have this weird glitch happening since I installed Ubuntu. I recently wipe my computer clean of Vista and formatted the hard drive. I have the most recent version of Ubuntu installed. 

Whenever I close my laptop and leave it closed for any time it doesn't run right when I open it back up. The right mouse button goes crazy and if left idle the pointer slowly moves to the left and down. I've tried wiping the touch pad and making sure the pad isn't dirty. I also tried plugging in the USB wireless mouse I use but it still goes crazy. If its left on the desktop it keeps creating new empty un-named folders. I have to reset the computer to get it to stop. 

This only recently started happening, it didn't do it for about the first 2 weeks of having Ubuntu installed. I just shut my laptop and go to work or the store and this happens. I have the settings set so that it doesn't go into sleep when the lid is shut.

Any ideas? this is really annoying problem.....

---

### Post by TwiztidChef on 2010-01-13
bump

---

### Post by Arch2 on 2010-01-14
try disableing the touchpad by entering this into terminal

sudo modprobe -vr psmouse

then reload it with...

sudo modprobe -v psmouse

---

