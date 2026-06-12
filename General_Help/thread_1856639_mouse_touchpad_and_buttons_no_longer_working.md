---
title: "mouse touchpad and buttons no longer working"
date: 2011-10-08
forum: General Help
---

### Post by humanoverdrive on 2011-10-08
hey guys, so this is the second time this has happened to me. the first time the only way i was able to resolve it was by completely deleting the ubuntu partition and doing a clean reinstall. now with it having occurred a second time i have been able to realize what caused it.

i am using an hp tx2500 tablet pc (thank god for the fact that it is a tablet, b/c without the stylus i would have no way to interface with the mouse) running 64-bit 10.04. my computer has a button on the keyboard that locks the touchpad and mouse buttons when enabled. after clicking this button, as one would expect, the touchpad and mouse buttons are disabled; however, when this button is disabled, the touchpad and mouse buttons STILL NO LONGER RESPOND to ANY input.  what is interesting to note is that after restarting the computer, when i reach the login screen, the touchpad and mouse buttons work PERFECTLY. it is only after entering my credentials and logging back on that the touchpad and buttons cease to function yet again. i have done multiple restarts with the same result. please help guys, i really dont want to have to reinstall ubuntu again just to fix this stupid problem.

Thanks!

---

### Post by Favux on 2011-10-09
Hi humanoverdrive,

Try this solution:  [http://ubuntuforums.org/showpost.php?p=10507107&postcount=8](http://ubuntuforums.org/showpost.php?p=10507107&postcount=8)

---

### Post by humanoverdrive on 2011-10-09
> **Favux said:**
> Hi humanoverdrive,

Try this solution:  [http://ubuntuforums.org/showpost.php?p=10507107&postcount=8](http://ubuntuforums.org/showpost.php?p=10507107&postcount=8)

You sir, are my new best friend lol. Thank you so much! This solution worked perfectly! I had been searching for something like this before posting this thread, but I guess I just didn't look hard enough. Thanks again man.

---

### Post by humanoverdrive on 2011-10-09
while the solution you posted works for the problem mentioned here, i was wondering if you knew anything about why my keyboard stops working and why i am unable to interface with the panel upon clicking and then unclicking the same "lock trackpad" button that caused the original problem. the keyboard and panel both work again after a restart.

---

### Post by Favux on 2011-10-09
Sorry, I'm not sure what you mean by panel?

Does the keyboard stop working after a suspend or hibernate?

---

### Post by humanoverdrive on 2011-10-09
the panel on the top of your screen, where the applications menu, places menu, system menu, power menu, etc. are

---

### Post by Favux on 2011-10-09
Not sure but you could try adding *i8042.reset* to the kernel's boot command line in Grub.  See:  [http://ubuntuforums.org/showpost.php?p=8211252&postcount=8](http://ubuntuforums.org/showpost.php?p=8211252&postcount=8)  I think this may be partially related to the BIOS.  But it is likely to late to update the BIOS from HP if you don't have the latest one.

---

### Post by humanoverdrive on 2011-10-09
Thanks. Yea I have the most up to date BIOS. I only recently switched over to Ubuntu and I flashed the BIOS not too long before I made the switch. As for adding the *i8042.reset *line, before I do that, I was hoping you could tell me what that does? I don't like messing around with kernel or grub if I don't know what it is I'm doing to it.

---

### Post by Favux on 2011-10-09
It resets the keyboard controller.

---

### Post by humanoverdrive on 2011-10-09
Thanks, I'll give it a try

---

### Post by humanoverdrive on 2011-10-09
didn't work. but thanks. since i hardly ever use that button and it fixes itself on a rest its not that big of a deal

---

