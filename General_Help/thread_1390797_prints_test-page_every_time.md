---
title: "prints test-page every time"
date: 2010-01-26
forum: General Help
---

### Post by jolns on 2010-01-26
I am slowly trying to learn and switch over to Linux/Ubuntu 9.10 karmic from Windows. So far so good. No major problems. (Haven't done much with the commands yet,) All installs and downloads have gone well so far. Except that my printer (HP psc1315 All in One) seems to have a hiccup. It prints a test-page every time I turn it on. How does one fix that little annoying glitch?

---

### Post by plucky on 2010-01-26
> **jolns said:**
> I am slowly trying to learn and switch over to Linux/Ubuntu 9.10 karmic from Windows. So far so good. No major problems. (Haven't done much with the commands yet,) All installs and downloads have gone well so far. Except that my printer (HP psc1315 All in One) seems to have a hiccup. It prints a test-page every time I turn it on. How does one fix that little annoying glitch?

Is that an HP test page or an Ubuntu Test Page?

---

### Post by jolns on 2010-01-30
> **plucky said:**
> Is that an HP test page or an Ubuntu Test Page?
I can't tell. I sorta looks generic. The drawing resembles the printer. It doesn't say HP anywhere.

---

### Post by plucky on 2010-01-30
Go to **System > Administration > Printing** and select your printer and see if there is a printer test job stuck in the queue.

Also try to power up the printer without it being connected to the system and see if it still prints out a test page.

You could delete the printer and then add it again and see if that fixes the problem.

Another good troubleshooting tool is the CUPS interface in Firefox.
In the address bar copy and paste ```
http://127.0.0.1:631/admin
``` will open the CUPS interface for your printer.

Good Luck

---

