---
title: "Printer not working"
date: 2006-02-02
forum: General Help
---

### Post by fakie_flip on 2006-02-02
I have a HP Deskjet 722 printer. When I add a printer in Ubuntu, Ubuntu gives the option to use a detected printer. It is detected as a Deskjet 720C, but mine is a 722C. After I add the detected printer and choose the the Deskjet 722C driver for it, I can goto System>Administration>Printing, and the printer says Ready. From there I try to print a test page, and it says test page sent to printer, but my printer does not do anything. I right clicked my printer and went to properties. There it says "Status: Ready: open device failed; will retry in 30 seconds..." My printer worked with Ubuntu Hoary HedgeHog, but not now in Breezy Badger. What can I do to get it working?

---

### Post by fakie_flip on 2006-02-02
Nevermind. I fixed the problem by editing /etc/pnm2ppa.conf. It looked like this:

version
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

I changed it to this:

version 720
#version 720 # 710, 712, 722 also acceptable
#version 820
#version 1000

Then I printed a test page, and it worked.

---

### Post by johnnymo87 on 2006-02-02
nice

---

