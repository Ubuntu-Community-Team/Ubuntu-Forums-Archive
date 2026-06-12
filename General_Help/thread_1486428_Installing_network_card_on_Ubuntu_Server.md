---
title: "Installing network card on Ubuntu Server"
date: 2010-05-17
forum: General Help
---

### Post by itsols on 2010-05-17
Hi, I believe my old pIII Dell's network card running Ubuntu server 8.04 is busted. I need to replace it.

I'd appreciate any advice on how to go about this. Do I just install the card and does it auto-install drivers or is there something else to do?

Many thanks!

---

### Post by jbrown96 on 2010-05-17
Shouldn't have any trouble replacing it. just check ```
ifconfig
``` to see if it shows up after you power up.

---

### Post by itsols on 2010-05-17
Thank you jbrown96 !

So if I don't see it, does it mean something else could be wrong?

Thank you!

---

### Post by jbrown96 on 2010-05-17
Perhaps, you could also try ```
lspci | grep Ethernet
``` to see if the card is physically recognized. The first command will report it if it is working properly. The second if Linux detects it.

---

### Post by itsols on 2010-05-17
Thank you once again. I shall try this.

Cheers!

---

### Post by cllow2020 on 2010-05-21
how to i know motherboard build-in lan is support wake on lan(WOL) ?

---

### Post by JoelOl75 on 2010-05-21
WOL options should be in the BIOS settings if supported

---

