---
title: "Virtualbox Printer issues"
date: 2010-07-18
forum: General Help
---

### Post by Cpierce on 2010-07-18
Having problems setting a printer for a VB machine. 10.04 host and XP guest. I have additions installed. I added the printer to the USB devices on the machines "details" page. Once I start the machine, and go to devices, the printer is there but is "grayed" out.

How do I fix this ?

---

### Post by howefield on 2010-07-18
Have you added the user to the vboxusers group ?

---

### Post by Cpierce on 2010-07-18
Howefield, I guess I don't know what you mean, so I assume I haven't. Can you explain ?

---

### Post by davidmohammed on 2010-07-18
goto administration - users and groups.

click manage groups - select vboxusers and click properties.  Tick your login name to add yourself to this group.

---

### Post by Cpierce on 2010-07-18
I did this, and will check it tomorrow. I sure appreciate to the help.

---

### Post by Cpierce on 2010-07-24
That fixed my problem !  Thank you

---

