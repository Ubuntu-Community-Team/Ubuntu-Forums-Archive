---
title: "memory card reader not working?"
date: 2011-11-09
forum: General Help
---

### Post by linuxaddix on 2011-11-09
running ubuntu 11.10 and noticed my built in card reader is not working.used it on a friends amd64 and works fine but when i use mine on my dell i get no response.the sd card worked with mint 11 why not now?is there a fix for this?

---

### Post by crazy bird on 2011-11-09
Type this command in a terminal: > lspci and paste the output here.
 
Also what you can do is open your caae and check if all the cables are still connected.

---

### Post by linuxaddix on 2011-11-09
sorry i have  Ricoh Co Ltd R5C822

---

### Post by linuxaddix on 2011-11-09
if anyone else needs it heres how to do it:
in terminal

gksu gedit /etc/modules

now enter this under the last line

sm_ftl
restart computer and there you go

---

### Post by crazy bird on 2011-11-09
> **linuxaddix said:**
> sorry i have Ricoh Co Ltd R5C822
 
But did you tried that command? It is good that you post the brand/model/type of your card reader, but we need to be sure that Linux sees is as well. And therefor you have to use that command.

---

### Post by linuxaddix on 2011-11-09
what?i dont understand your english and yes it worked if it didnt i wouldnt have changed it to solved and directions how to do it

---

### Post by crazy bird on 2011-11-09
> **linuxaddix said:**
> i dont understand your english 

is that my gratitude to you for trying to help you? An insult?

---

### Post by linuxaddix on 2011-11-09
guy enough.its already solved.thanks anyway.help is no longer needed read the title as it says solved

---

### Post by doncletus on 2011-12-28
> **linuxaddix said:**
> if anyone else needs it heres how to do it:
in terminal

gksu gedit /etc/modules

now enter this under the last line

sm_ftl
restart computer and there you go

thanks!!! this quickly solved my problem!

---

