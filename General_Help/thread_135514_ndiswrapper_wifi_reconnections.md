---
title: "ndiswrapper wifi reconnections:"
date: 2006-02-24
forum: General Help
---

### Post by klepto on 2006-02-24
This is something that is really irritating me.
Whenever I need to reconnect my wifi access I have to
reboot the machine in order to get an ip addy. 
I can restart the network interfaces and other things
but I won't recieve an ip address but when I reboot.. 
I get an ip address quickly.. 

Any idea if this is a bug and if there's a fix?

---

### Post by greatshape on 2006-02-24
Possible workaround:
```

sudo dhclient eth1

```

(assuming eth1 is your wlan interface)

sincerely steve

---

