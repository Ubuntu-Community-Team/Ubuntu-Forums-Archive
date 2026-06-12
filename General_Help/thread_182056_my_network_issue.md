---
title: "my network issue"
date: 2006-05-25
forum: General Help
---

### Post by Melciah on 2006-05-25
ive recently installed a ubuntu server on an old p2 box. the install went fine but networking isnt working. i cant update at all. the first repo hangs at 66% and after a good deal of time, it fails completely.

the local network is controlled by my adsl modem using dhcp, in case this info helps.

---

### Post by _linux_ on 2006-05-25
What networking card are you using? Is it wireless?

---

### Post by El Menda on 2006-05-25
When u are surfing on the net have u got any problem? Have u tried to download a big file or something?

---

### Post by Melciah on 2006-05-25
hey fellas. i couldnt tell you what nic card it is from memory. i can tell you that its a simple 10/100 pci card and is not wireless.

when i said it was a server, i really mean it. command line only. so web downloading is not really an option.

i can also tell you that i manage to get both the web and the update manager working with it in vector linux not too long ago, without any trouble.

ill post the actual make and model of the card when i get home later. 

cheers

---

### Post by jvictor on 2006-05-26
These are my suggestions

1) Disable ipv6
2) Try using a static ip
3) Use ur ISPs DNS server in /etc/resolv.conf

That sould solve your issues

---

### Post by Melciah on 2006-05-26
youre my favourite person in the whole wide world right now jvictor. it worked like a charm. thanks

---

### Post by jvictor on 2006-05-26
NP :) we're here to helpout each other

---

