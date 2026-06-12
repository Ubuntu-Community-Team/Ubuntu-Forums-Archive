---
title: "wireless drop"
date: 2010-08-02
forum: General Help
---

### Post by choochoousmc on 2010-08-02
every so often Ubuntu 10.04lts will drop the wireless connection.
Only way to regain is to shut down and reboot.
Is there any way to prevent , repair, or force a reconnect without rebooting?

---

### Post by Smart Viking on 2010-08-02
I have no idea of this will work but you could try to launch the following command(it should stop the network manager and Ubuntu will automatically launch it again):

```
sudo pkill Network
```

:)

---

