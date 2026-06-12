---
title: "Senao wireless card not working with InitNG!"
date: 2006-04-18
forum: General Help
---

### Post by k00zk0 on 2006-04-18
I just bought a Senao NL2511CD PLUS EXT2 wireless card, and it uses the Prism 2.5 chipset, so its supposed to work natively in linux.

If I start up Breezy with the normal init it will start the card (LED turns on) while it says "Setting up ALSA Card 0" or somethign similar to that, and it will correctly register the eth0 interface in the networking setup, and allow me to connect, but when I start up Ubuntu using InitNG, it will start up the LED on the card when something related to "coldplug" flashes by, but the card wont show as eth0 or anything in Ubuntu.

It wont start up if I try ejecting the card and reinserting it, and I've tried adding system/pcmcia to my /etc/initng/system.runlevel file, to no avail.

Any help appreciated in getting it to work with InitNG, Thanks.

---

### Post by k00zk0 on 2006-04-18
More info, when I boot up, about a second before it starts X and goes into a GUI from the console style text, some text scrolls by with eth0 and the word "error" in the last line. That's about all I can catch of it. Shift+Pageup doesnt let me scroll up high enough to read it. Is there some sort of log written from the startup?

---

### Post by k00zk0 on 2006-04-20
Bump.

Anyone?

---

