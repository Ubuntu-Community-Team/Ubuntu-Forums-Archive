---
title: "ubuntu network installation guide for dummy"
date: 2009-12-20
forum: General Help
---

### Post by manuleka on 2009-12-20
i'm just curious to try this out... never done this kinda setup before -

i wanna make my main pc (running Ubuntu 9.10 Desktop) be able to server installable images so when i want to install OS on other pcs i can easily do so through the network...

to start of with, i've got an MSI WIND that i want to install Ubuntu 9.10 remix on... i have the image on my pc, i can use a usb stick but i want to learn how to do this setup (so i can use for other OS)

cheers for any help in advance :)

---

### Post by hugmenot on 2009-12-20
Your "server" needs a DHCP server and a TFTP server to transmit the image. Then you need pxelinux also on the server.

Just google pxelinux for starters.

---

