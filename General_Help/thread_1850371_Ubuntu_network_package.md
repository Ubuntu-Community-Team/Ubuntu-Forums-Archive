---
title: "Ubuntu network package?"
date: 2011-09-26
forum: General Help
---

### Post by Zeta-K on 2011-09-26
What packages does ubuntu use to auto-detect and auto-connect to ethernet networks. My other distroes have to be manually configured from a rescue cd every time I want to connect to a network that I haven't used before and it's getting a bit redundant.

---

### Post by matt_symes on 2011-09-26
Hi
```

matthew@matthew-laptop:/sys/bus/usb$ dpkg -l | grep network-manager
ii  network-manager                       0.8-0ubuntu3.2                                  network management framework daemon
ii  network-manager-gnome                 0.8-0ubuntu3                                    network management framework (GNOME frontend
ii  network-manager-pptp                  0.8-0ubuntu3                                    network management framework (PPTP plugin)
ii  network-manager-pptp-gnome            0.8-0ubuntu3                                    network management framework (PPTP plugin, G
matthew@matthew-laptop:/sys/bus/usb$
```

Kind regards

---

### Post by Zeta-K on 2011-09-26
> **matt_symes said:**
> Hi
```

matthew@matthew-laptop:/sys/bus/usb$ dpkg -l | grep network-manager
ii  network-manager                       0.8-0ubuntu3.2                                  network management framework daemon
ii  network-manager-gnome                 0.8-0ubuntu3                                    network management framework (GNOME frontend
ii  network-manager-pptp                  0.8-0ubuntu3                                    network management framework (PPTP plugin)
ii  network-manager-pptp-gnome            0.8-0ubuntu3                                    network management framework (PPTP plugin, G
matthew@matthew-laptop:/sys/bus/usb$
```Kind regards

Thanks.

---

