---
title: "how to perform restart from command line after upgrade?"
date: 2011-10-14
forum: General Help
---

### Post by robjmarquez on 2011-10-14
Hello,
        I performed the upgrade from natty narwhal on my laptop. Instead of clicking on restart, I shutdown the laptop. Now when I boot, it gives me the splash screen saying it's waiting for network configuration.  Then the screen goes blank after about 2 minutes. Never get anything more. So I hit ctrl-alt-f1, and logged in as root there. It immediately says the system needs to be rebooted to reconfigure,  but I have tried shutdown -r, and reboot with nothing changing. 

How do I tell it to reboot and reconfigure so I can get my x-display back?

thank you.

---

### Post by robjmarquez on 2011-10-14
This fixed my issue. Read the whole page to get everything needed to fix.
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

Still having issue where I don't get my launcher, or any options to shutdown or even logout. This part is ridiculous.

---

