---
title: "Additional drivers not working"
date: 2012-07-18
forum: General Help
---

### Post by Lncredible on 2012-07-18
Hi all,

I have just installed 12.04 64-bit Ubuntu side by side with Windows 7 - first time using Linux on my home machine.

Happy so far, although my sound quality seems to be pretty poor on the Linux boot, compared to Windows. I assumed that this would be to do with the wrong driver being used, so I tried using 'Additional Drivers' from the 'System Settings' area. 

When I do this, I only seem to get the same old message about proprietary drivers being used for my wireless card. The thing is, the driver is listed as activated and currently in use, but I can't seem to dismiss the window to continue searching for other driver issues. Is this because Ubuntu thinks there are no other problems? It always returns to the same 'issue' (but the wireless is absolutely working fine).

Grateful for any assistance! Thanks!

---

### Post by Cheesemill on 2012-07-18
Your sound quality is as it should be, Windows applications artificially boost your sound so that it is different to the actual data on your computer.

Try adjusting the treble and bass controls on your speakers instead.

---

### Post by Lncredible on 2012-07-18
> **Cheesemill said:**
> Your sound quality is as it should be, Windows applications artificially boost your sound so that it is different to the actual data on your computer.

Try adjusting the treble and bass controls on your speakers instead.

OK I'll give that a shot.

Any thoughts on the driver issue? Any other way I can check that all my other drivers are working correctly?

---

### Post by Cheesemill on 2012-07-18
> **Lncredible said:**
> OK I'll give that a shot.

Any thoughts on the driver issue? Any other way I can check that all my other drivers are working correctly?

If the hardware is working then all of the drivers are installed.
Linux drivers are all built into the kernel, the major exception to this is closed-source graphics drivers which can be installed by opening the 'Additional Drivers' application.

If this doesn't show any results then all of your drivers are installed and up to date.

---

### Post by Lncredible on 2012-07-18
> **Cheesemill said:**
> If the hardware is working then all of the drivers are installed.
Linux drivers are all built into the kernel, the major exception to this is closed-source graphics drivers which can be installed by opening the 'Additional Drivers' application.

If this doesn't show any results then all of your drivers are installed and up to date.

So shall I ignore the relentless wireless driver message, that proposes no solution?

---

### Post by Cheesemill on 2012-07-18
Which message is this?

Could you post either the text of the message or a screenshot of the dialog box please.

---

### Post by Lncredible on 2012-07-18
'Proprietary drivers are being used to make this computer work properly.

.........

(Green circle) Broadcom STA proprietary wireless driver

Tested by the Ubuntu developers
Licence: Proprietary
This package contains ....................

(Green circle) This driver is activated and currently in use.'


The options I have are "remove" "help" and "close", yet if I close the window, it will simply return again.

---

### Post by Cheesemill on 2012-07-18
If it's activated then it is already installed, you don't need to do anything else.

Everything is working as it should be.

---

