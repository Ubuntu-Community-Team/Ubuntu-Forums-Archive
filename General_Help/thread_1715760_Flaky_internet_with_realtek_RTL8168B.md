---
title: "Flaky internet with realtek RTL8168B"
date: 2011-03-27
forum: General Help
---

### Post by linuxman94 on 2011-03-27
As the title says, i am having problems with my realtek onboard ethernet.  I have installed the driver for it but sometimes it will randomly stop working.  See this [thread]("http://ubuntuforums.org/showthread.php?t=1708465") for more info on the hardware.  My computer specs are in my sig.

EDIT: The chip is acctually a Realtek 8111D

---

### Post by linuxman94 on 2011-03-28
Kind bump

---

### Post by linuxman94 on 2011-04-03
bump again

---

### Post by Mark Phelps on 2011-04-04
I have a similar problem with a different Gigabyte motherboard and Realtek LAN chip -- but it manifested itself when I booted back into Ubuntu 10.10 from Windows 7.

Something in Windows was intermittently disabling the LAN chip such that, when I booted into Ubuntu, sometimes, I would get no network.

I was able to fix that some of the times because the Gigabyte website had a downloadable Reltek LAN diagnostic utility.  I ran that and sometimes, the LAN would still work.

It's taken three driver updates, but now, the LAN works all the time.

If you're only running Ubuntu, sorry, don't have any way to force the LAN to work as all the diagnostics and driver updates were done in Windows 7.

---

### Post by linuxman94 on 2011-04-05
Thanks for the response.   I have decided that the problem is with my linksys router because all the computers in the house reproduce the issue at the same time.  I'm gonna install DD-WRT and that should fix it.

---

