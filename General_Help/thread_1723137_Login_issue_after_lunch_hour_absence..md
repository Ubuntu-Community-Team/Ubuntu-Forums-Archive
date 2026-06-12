---
title: "Login issue after lunch hour absence."
date: 2011-04-06
forum: General Help
---

### Post by chrishoffman on 2011-04-06
After returning from lunch or over night my screen brings up the login window but says "Checking" and this goes on for a long time. I end up doing the Ctrl, Alt, Backspace so I can go back to work but it is getting old. I am running 8.04 on Dell Dimension 4600 with dual viewsonic VP930 screens and Matrox video card, if that helps. If I do the Ctrl, Alt, F1, I get this message.

kinit-trying to resume from /dev/desk/by-uuid/4795015e, ...
kinit: no resume image, doing normal boot...
Ubuntu 8.04.3 LTS us 137 Hy1
us137 login

Any suggestions would be greatly appreciated. I am pretty green with this Ubuntu forum process but it looks like a very helpful tool.

---

### Post by techunit on 2011-04-06
Have you attempted a reboot? That seems like the best course of action. 

Now if that doesn't work can you force exit? or su into another account from a virtual terminal?

---

### Post by 3Miro on 2011-04-06
It seems while you are away, Ubuntu puts the HDD to sleep and then it has hard time waking up. You can either set the power manager to not go to sleep, or you can upgrade to something newer than 8.04. The support for 8.04 ends by the end of the month, so it is highly recommended that you upgrade. 10.04.2 is probably the best bet for you.

---

