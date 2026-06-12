---
title: "printing letter instead of A4 paper format"
date: 2009-12-20
forum: General Help
---

### Post by Jurjen de Vries on 2009-12-20
When I open a program the default of page setting paper format is letter. This is strange because the default settings of the printer are A4, and I also changed the settings in /etc/papersize from letter to a4. The program will save my setting, but when I open another (new) program, the default is letter to.

My printer is a Dell MFP 3115cn

Thanks for helping.

---

### Post by SuperSonic4 on 2009-12-20
Have you looked in printer options, I'm not sure where the GUI is

---

### Post by Jurjen de Vries on 2009-12-20
Thanks for quick reply.
I've looked in System > Administration > Printing
From there I clicked my printer, printer options and the media size there is A4.

---

### Post by dcstar on 2009-12-20
> **Jurjen de Vries said:**
> When I open a program the default of page setting paper format is letter. This is strange because the default settings of the printer are A4, and I also changed the settings in /etc/papersize from letter to a4. The program will save my setting, but when I open another (new) program, the default is letter to.


Check that your locale is correct: /etc/default/locale

---

### Post by Jurjen de Vries on 2009-12-20
jurjen@jurjen-desktop:/etc/default$ more locale 
LANG="en_US.UTF-8"

I guess this is correct? I've installed Ubuntu with English language. What should a language had to do with the paper media size?

---

### Post by Leppie on 2009-12-20
does this happen with only 1 specific program, or all programs?
have you tried looking at the settings in the cups admin page?
[http://localhost:631/](http://localhost:631/)

---

### Post by Jurjen de Vries on 2009-12-20
Now it's working. Not do cups. But I guess due a reboot. I never rebooted , and due something else I had to reboot.
Could it be that /etc/papersize need a trap?

---

