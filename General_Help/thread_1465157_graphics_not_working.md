---
title: "graphics not working"
date: 2010-04-29
forum: General Help
---

### Post by surrealillusions on 2010-04-29
Hi all,

On bootup, it went into the BIOS with the time/date out (going back to the manufacturing date), after that, it doesn't boot up properly, get a maintenence shell, type 'fsck', then 'y' to repair, then reboot.

On logging in, I have to change the time manually.

However..although everything seems to work, the graphics card is not working.
Its an ATI card, and the catalyst program is in the Applications menu, although it doesn't work.

I've tried downloading the drivers from ATI's site, but the file doesn't run.

It seems to recognise theres a card there (by going to system - adminstration - hardware drivers), but doesn't seem to understand that it can use it.

How do I reinstall the graphics card or reinstall the drivers?

Thanks.

---

### Post by Mark Phelps on 2010-04-29
Need to know the model of the card (e.g., HD 5870, X1650, X200).

Were the graphics working before?  What have you done since then to the PC?

---

### Post by surrealillusions on 2010-04-29
The model is an ATI Radeon HD4350.

I managed to install the drivers via terminal after looking up the correct command:

sudo sh name-of-file.run

And then went through the install process, and the catalyst program now works, and the graphics appear to be better..(for instance the scrolling in the web browser isnt jumpy now).

The graphics have been working perfectly fine for months and have done nothing to the PC. Just switched it off last night, went to sleep, then woke up..switched on, and then encountered the problem. The computer hasn't moved or anything.

---

