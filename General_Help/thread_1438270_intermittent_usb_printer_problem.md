---
title: "intermittent usb printer problem"
date: 2010-03-24
forum: General Help
---

### Post by pernest on 2010-03-24
Hi,

I really need some diagnosing help. I have a parallel port printer connected using usb->parallel adapter. Sometimes the printer prints sometimes it doesn't.

A job will go the print queue and then sit there for ages. Sometimes if I unplug and then replug the usb->parallel cable the printer will print other times it will print half the document then freeze until the cable was unplugged and replugged again.

The printer never shows up in the list using lsusb (only my usb mouse and scanner do).

The printer is an hp deskjet 690c and worked fine under WinXP through a normal parallel cable. The one thing I haven't tested (but will test tomorrow) is the usb->parallel cable in XP.

Any help with would be very much appreciated.

---

### Post by quixote on 2010-03-26
Well, I'm not sure this helps your actual problem, but are you aware of CUPS admin via the browser?  You can cancel jobs, or force a printer to resume without replugging the cable.  I'm not sure it's any less tedious, but it'll save wear and tear on the plugs. 

Type "http://localhost:631" (without quotes) in your browser's url bar.  Very few operations are permitted without root access.  When it asks you for that login, older CUPS wanted "root" and the password for your primary user.  The newest versions just want your primary username and password.

One thing I've found when printers behave as you describe is that the problem can be old jobs stuck in the queue.  Then the CUPS admin page actually solves the real problem, since that's the only way to really purge them.

---

