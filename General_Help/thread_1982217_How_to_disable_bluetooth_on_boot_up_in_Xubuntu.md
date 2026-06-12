---
title: "How to disable bluetooth on boot up in Xubuntu?"
date: 2012-05-18
forum: General Help
---

### Post by Marzata on 2012-05-18
How to disable bluetooth on boot up in Xubuntu 12.04 LTS? Thank you!

---

### Post by lightning slinger on 2012-05-18
Settings Manager>Session and Startup>Application Autostart>Blueman Bluetooth Manager (uncheck)>Close

---

### Post by Toz on 2012-05-18
To disable the bluetooth service from starting at boot:
```
sudo update-rc.d -f bluetooth remove
```

---

### Post by Marzata on 2012-05-18
Thanks but how to enable it later on?

---

### Post by Toz on 2012-05-18
```
sudo update-rc.d bluetooth defaults
```

You can find more information in the update-rc.d man page:
```
man update-rc.d
```

---

