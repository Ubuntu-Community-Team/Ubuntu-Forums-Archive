---
title: "Internet wont connect even with ethernet cable"
date: 2010-03-28
forum: General Help
---

### Post by jcdavies on 2010-03-28
I have a toshiba satellite laptop and originally tried to use ubuntu with my wireless network but was unsuccessful, so then thought i would just use it connected to the router with a cable as you would usually do with a desktop and as i have had done with a desktop in teh past, where i never had an issue connecting to the net if the cable was in then i was connected.

However on my laptop this is not the case when i plug in a ethernet cable ubuntu detects taht i have done this and searches for the connection but then does not connect.

Why is that and how can i rectify it?

---

### Post by bobcollard on 2010-03-28
> **jcdavies said:**
> I have a toshiba satellite laptop and originally tried to use ubuntu with my wireless network but was unsuccessful, so then thought i would just use it connected to the router with a cable as you would usually do with a desktop and as i have had done with a desktop in teh past, where i never had an issue connecting to the net if the cable was in then i was connected.

However on my laptop this is not the case when i plug in a ethernet cable ubuntu detects taht i have done this and searches for the connection but then does not connect.

Why is that and how can i rectify it?
Turn off your Modem and your router  for about 15 seconds to give them time to reset.  You might also try the following command in Terminal to restart the network:
                                 ```
sudo /etc/init.d/networking restart
```

---

