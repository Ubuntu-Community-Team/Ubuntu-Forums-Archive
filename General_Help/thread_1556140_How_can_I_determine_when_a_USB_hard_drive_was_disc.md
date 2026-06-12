---
title: "How can I determine when a USB hard drive was disconnected?"
date: 2010-08-19
forum: General Help
---

### Post by zugvogel on 2010-08-19
Hi,

Is there any way to tell the time and date when a USB hard-drive was disconnected? It may have been disconnected through power failure (although the computer continued running) or it may have been disconnected manually.

Thanks!

---

### Post by jobix on 2010-08-19
Did you try checking the /var/log/messages file? You could also write a small script that checks if the usb drive is there every minute or so and logs an entry or timestamp with the time it was last there. Use lsusb. It depends on how precisely you want to know the time. Just curious, what is the purpose of this? Maybe if the objective is spelled out, others can give you better solutions.

---

### Post by zugvogel on 2010-08-19
Thanks Jobix - your suggestion was really helpful.
The reason for asking is simply to identify the reason for losing USB access, and knowing the time can help.

In this case the messages file shows both a disconnecting of the USB drive and loss of ethernet connection at the same time. This suggests a power failure in the building (the computer is unaffected since it has a battery but the USB drive requires external power, as does the router).

Thanks for your help!

---

