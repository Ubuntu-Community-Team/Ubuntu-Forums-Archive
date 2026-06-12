---
title: "Multiple USB com port addressing"
date: 2011-01-20
forum: General Help
---

### Post by U-Toto on 2011-01-20
Hello,
I have 2 xbee explorer USB boards hooked into my Acer Netbook running 10.04. I have successfully mapped the /dev/tty/USB0 and set it up as com2 to use with X-CTU XBee software.  It works. WHen I try to have a 2nd USB explorer board and do the same mapping thy both show as the same manufacturer so the same address(006). Even though the second reads as /dev/tty/USB1. Has anybody ran into this situation as well?

Thanks.-

---

### Post by U-Toto on 2011-01-20
Hasn't anybody ever had 2 of the same manufacturer USB/serial mods plugged in to a 10.04 machine at the same time? Only the first one plugged in can be used because although they show as /dev/tty/USB0 and 1, they share the same manufacture code and so get the same address. This cannot be an isolated incident.
 Anybody?  Please?

---

