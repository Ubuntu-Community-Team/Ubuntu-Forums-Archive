---
title: "equivalent commands?"
date: 2011-11-02
forum: General Help
---

### Post by JAZ1976 on 2011-11-02
Does Ubuntu server 11.04 have an equivalent command for HP-UX's enable, disable and lpalt commands?

---

### Post by ibutho on 2011-11-02
What are the commands you listed, used for?

---

### Post by haqking on 2011-11-02
Depends on what you have installed. if you have CUPS or Smaba installed then yes as far as i know. ? i think

They are just print commands

---

### Post by JAZ1976 on 2011-11-03
ibutho, the commands are used to disable and enable a printer. The other command lpalt is used to change the output printer of a spooled job. I am porting a program over from an old HP-UX system and I need to know what commands in Ubuntu Linux I can use in the functions that preform these tasks within the program.

---

### Post by JAZ1976 on 2011-11-03
haqking, I have CUPS installed on the server.

---

### Post by JAZ1976 on 2011-11-07
Guys,

I have found the cups commands to enable and disable the printers, they are cupsenable and cupsdisable. As for the lpalt command which alters the print job request I think that the lpmove command may work, but I am not sure yet.

---

