---
title: "NetworkManager disabled, need to enable."
date: 2009-08-01
forum: General Help
---

### Post by Peacefulpieofdeath on 2009-08-01
Ok i fallowed (yes im stupid) a guide to give me a static ip, it failed. But in the prosses i thought i was disabling my networkmanager temporaraly with this comand:

> sudo update-rc.d NetworkManager removeNow when i boot there is no internet, the only way i can start it is by typing:

> sudo service NetworkManager startCan someone tell me how to make it start at boot again, thx.

****Fixed thanks x33a****

---

### Post by x33a on 2009-08-01
try
```
sudo update-rc.d NetworkManager defaults
```

---

