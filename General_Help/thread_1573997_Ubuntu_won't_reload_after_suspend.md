---
title: "Ubuntu won't reload after suspend"
date: 2010-09-13
forum: General Help
---

### Post by Oven Glove on 2010-09-13
I've just installed 10.04 in dual boot with xp, completed all updates and tried to suspend. My swap partition is the right size and I don't recall doing anything wrong yet when I wake up the computer after suspending it, the monitor doesn't reactivate and I've had to force it to shut down. And also, now it tells me "networking disabled" GRRR!!

Any suggestions would be great.

Owen.

---

### Post by Taiji on 2010-09-13
I am not sure this function ever really worked properly.

---

### Post by xircon on 2010-09-13
```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Change false to true

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```

Happened to me :lol:

:edit: and reboot!!

---

