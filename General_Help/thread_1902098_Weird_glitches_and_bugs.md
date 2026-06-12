---
title: "Weird glitches and bugs?"
date: 2011-12-30
forum: General Help
---

### Post by onipar on 2011-12-30
I'm running Ubuntu 11.10 on a brand new system I built ( Gigabyte 880gma-usb3, AMD phenom II X3, 1 T Hdd, 8 GB G skills Ram), and I'm experiencing a number of glitches and bugs that I don't know how to fix.

The first and most prevelant that I noticed was the system occassionally freezing when I either try to "restart" or "switch users."  With both freezes it usually goes to the purple Ubuntu screen and then gets stuck.  It doesn't happen every time, but often enough.

The next glitch is second most often occurring.  I forget what it's called, but you know how you can drag a window to the side, and this orange-ish box appears to show you were the window will lock into place?  Well sometimes that orange box appears and doesn't go away until I click the window management thingy and then back off it.

And finally, most recent and least pervasive, when i was trying to empty the trash, the little bubble pop up that says "Empty trash" wouldn't go away, and then the unity bar wouldn't "hide" when i had a browser window open.  Fixed this with a restart (which froze first).

I'm not sure if these are related issues, or if it's something simple like I need to update something, but any help is greatly appreciated.

Thanks!  :D

---

### Post by Paddy Landau on 2011-12-30
This sounds like a hardware incompatibility.

Open Additional Drivers (while connected to the Internet) and see if it lists any extra drivers. If it does, enable them and see what happens.

Otherwise, I'm sorry, I am at a loss as to what to do next.

---

### Post by onipar on 2011-12-30
> **Paddy Landau said:**
> This sounds like a hardware incompatibility.

Open Additional Drivers (while connected to the Internet) and see if it lists any extra drivers. If it does, enable them and see what happens.

Otherwise, I'm sorry, I am at a loss as to what to do next.

Thanks!  In fact, under additional drivers, there are two graphics drivers that won't install (I've tried, and they just won't go all the way to the end).  At first I though they were unnecessary drivers (because I don't have a GPU), but I'm starting to think I might need them for the integrated video on my motherboard...

Any ideas of how to get the drivers to install, or find ones that will? :confused:

---

### Post by NilPointer on 2011-12-30
So, installation progressbar stucks at some point and doesn't increases at all? Or it fails silently? Maybe you just didn't give it enough time to finish installation?

Is there option to see terminal output when installing driver? If yes, then paste it's output.

---

### Post by onipar on 2011-12-30
Here's what it says when I open the additional drivers:

"No proprietary Drivers are in use on this system.  Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  Security Updates and corrections depend solely on the responsiveness of the manufacturer.  Ubuntu Cannot fix or imporve these drivers."

The drivers:

"ATI/AMD proprietary FGLRX graphics driver (Post-release updates)."
"ATI/AMD proprietary FGLRX graphics driver"

Neither of these have been or can be activated...

---

### Post by onipar on 2011-12-30
> **NilPointer said:**
> So, installation progressbar stucks at some point and doesn't increases at all? Or it fails silently? Maybe you just didn't give it enough time to finish installation?

Is there option to see terminal output when installing driver? If yes, then paste it's output.

Okay, I'll give that a shot

---

### Post by onipar on 2011-12-30
Okay, so I tried installing those drivers again, and the second one actually did work.  The first one however, (that says post release updates) still didn't work.  It said there is a log of why, but I'm not sure how to find it:   /var/log/jockey.log

I don't know how to get to it.

Also, I'm not sure how to get the terminal to show me what's it's doing while trying to install.  Any ideas?

---

### Post by Paddy Landau on 2011-12-30
Try rebooting. Has your problem been fixed? If not, try again to install the second one.

---

### Post by onipar on 2011-12-30
The one install took.  Rebooted.  No glitches yet!  

The second install is being stubborn.  But this might have fixed it.

---

### Post by Paddy Landau on 2011-12-31
If it's been fixed, don't install the second one, but just mark this thread as solved.

---

### Post by onipar on 2011-12-31
Yeah, I was just waiting to see if any of the glitches reoccur.  Once I realized it was a graphics/driver problem, i searched those drivers and it appears this is a fairly widespread problem, and depending on the type of video card, the driver may or may not work well.  I guess it seems these particular drivers are still "in flux."

---

### Post by Paddy Landau on 2011-12-31
Yes, drivers can be a problem with Linux, because many manufacturers write drivers only for Windows.

---

