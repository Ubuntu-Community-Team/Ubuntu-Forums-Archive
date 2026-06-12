---
title: "connect ubuntu 10.04 to internet via ethernet?"
date: 2010-12-07
forum: General Help
---

### Post by owners4life5 on 2010-12-07
hello,

i have two ubuntu 10.04 desktops, and one of them is connected to the internet wirelessly, while the other one is not connected at all.

is there any possible way i can connect the one without internet via an ethernet cable to the other one by using the wireless internet off of the other one?

thanks in advance,

---

### Post by 3rdalbum on 2010-12-07
Yes. On the wireless computer, right click the Network Manager applet and choose Edit Connections. Create a new wired connection and give it a name, and under the iPv4 tab choose "Shared to other computers".

Apply and save your changes. Plug in the Ethernet cable. If the wireless computer connects to "auto eth0" disconnect this in Network Manager, and connect it to your new wired connection. Finally, the other computer should be able to connect and get internet access through the wireless computer.

---

### Post by owners4life5 on 2010-12-07
> **3rdalbum said:**
> Yes. On the wireless computer, right click the Network Manager applet and choose Edit Connections. Create a new wired connection and give it a name, and under the iPv4 tab choose "Shared to other computers".

Apply and save your changes. Plug in the Ethernet cable. If the wireless computer connects to "auto eth0" disconnect this in Network Manager, and connect it to your new wired connection. Finally, the other computer should be able to connect and get internet access through the wireless computer.

this worked until i came to the step where i plugged in the cable. once i plugged it in, there was no Auto eth0 connection, and the connection i had just created did not show up. so what can i do now?

thanks for the rather quick reply, also.

---

### Post by owners4life5 on 2010-12-08
bump

---

### Post by owners4life5 on 2010-12-10
bump

---

### Post by owners4life5 on 2010-12-12
bump

---

