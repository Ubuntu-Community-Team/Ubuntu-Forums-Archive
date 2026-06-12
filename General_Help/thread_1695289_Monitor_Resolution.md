---
title: "Monitor Resolution"
date: 2011-02-25
forum: General Help
---

### Post by ColeTurner on 2011-02-25
I am using Ubuntu 10.10. It won't detect or let me change the monitor resolution. Will any of you help me?

---

### Post by grahammechanical on 2011-02-25
How are you trying to change the monitor settings? System>Preferences>Monitors? Have you installed a driver through System>Administration>Additional drivers?

I have a Nvidia driver activated. I get NVIDIA X-Server Settings utility but it does not let me change the monitor resolution. If I remember correctly, before I installed the Nvidia driver I could use the Monitors utility. It did not let me set the monitor resolution either. It is all done through the button Detect Displays.

To do what you want you may have to edit the X-Server configuration files.

I think that at boot time the X-Server utility probes the monitor to determine the optimum resolution and so we do not need to set the resolution ourselves. Get it wrong and we damage the monitor. Then we blame Ubuntu.

Regards.

---

### Post by ColeTurner on 2011-02-25
I am trying to make the resolution smaller.

---

### Post by Bcrowes11 on 2011-02-25
Go to System -> Preferences -> Monitors. It'll show the available desktop screen sizes for you. :guitar:

---

### Post by ColeTurner on 2011-02-25
It only shows one. On my old computer, it would show a lot of sizes. I am using the same monitor.

---

