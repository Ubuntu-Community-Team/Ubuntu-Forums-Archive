---
title: "shutdown in the mid of installation cause everything crash,no access to terminal"
date: 2010-08-08
forum: General Help
---

### Post by usiyalla on 2010-08-08
hai i got a huge problem here i was going with tutorial(mac theme and looks for ubuntu)

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

 but in the mid  when i was installing global menu my pc shut down (by electricity  problem) now i restart menu and panel area blinking nothing showing i  cant reach terminal our any system tool
now what can i do
i dont want to reinstall all things again 
i'm using ubuntu 9.04
dualboot with window xp

---

### Post by corrytonapple on 2010-08-08
First, put a period in there so its easier to read. ;) Next, boot from your live cd and open the terminal. Type:
```

sudo-apt get purge globalmenu

```
Restart from the Hard Drive. That _should_ do it but it might not. In the command it is uninstalling globalmenu. Hope it works.

---

