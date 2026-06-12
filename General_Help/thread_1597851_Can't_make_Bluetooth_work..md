---
title: "Can't make Bluetooth work."
date: 2010-10-15
forum: General Help
---

### Post by Sergius14 on 2010-10-15
Hi,

Im trying to get a Bluetooth USB dongle work but I cant.

Bluetooth Preferences doesnt recognise it and bluetooth manager gives me this error "Bluez daemon is not running, blueman-manager cannot continue.". See attached captures.

I already tried many solutions proposed in other threads with no luck. I reinstalled their packages and it keeps the same.

I'm using 10.10 upgraded from 10.04. With 10.04 I had the same issue.


What can I do?

---

### Post by Sergius14 on 2010-10-16
Bump

---

### Post by Sergius14 on 2010-10-17
Bump.

---

### Post by Sergius14 on 2010-10-18
Bump

---

### Post by Sergius14 on 2010-10-19
Bump

---

### Post by Sergius14 on 2010-11-13
Finally I solved it by my self.

Seams to be that somewhere in time the service bluetooth has change.
```

sudo /etc/init.d/bluetooth start
``` is not working anymore in latests Ubuntu releases.

I have to start bluez with ```
sudo bluetoothd -u
``` as a replacement of the previous one.

The bluetooth came to life and starting to work (very bad and unusuable, but that's another story).

---

### Post by aldeby on 2010-11-21
Thank you for reporting back your experience!

I would suggest you to completely uninstall every bluetooth package and then reinstall gnome basic ones and try blueman (you may install it from the repositories).

Ensure you leave the bluetooth device on at boot in Jupiter or Eee-control so that the bluetooth daemon can take control of it. Later you may disable the bluetooth device to save power from the bluez tray icon.

Cheers!

---

### Post by checoimg on 2011-03-08
I'll try this tomorrow night.

---

