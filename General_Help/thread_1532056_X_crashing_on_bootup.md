---
title: "X crashing on bootup"
date: 2010-07-15
forum: General Help
---

### Post by user1397 on 2010-07-15
So I had a faulty nvidia card, and I installed the proprietary drivers for it, but my computer kept screwing up, so I removed the card, and used the system VGA port (without uninstalling the proprietary drivers through the Hardware Drivers app).

So now everything works fine, except that everytime I bootup X crashes and gives me the option to restart it and some other things.

I can no longer uninstall the drivers officially through the Hardware Drivers app, because it doesn't show up there anymore.

So I tried manually uninstalling anything that had to do with xserver and nvidia, but I still get the startup crash.

I tried running sudo dpkg-reconfigure xserver-xorg but that didn't do anything.

Any thoughts?

---

### Post by user1397 on 2010-07-18
bump

---

### Post by lidex on 2010-07-18
Try removing xorg.conf and reboot. More problems, post your log file.
```
sudo rm /etc/X11/xorg.conf
```
```
cat /var/log/Xorg.0.log
```

---

### Post by user1397 on 2010-07-18
> **lidex said:**
> Try removing xorg.conf and reboot. More problems, post your log file.
```
sudo rm /etc/X11/xorg.conf
```
```
cat /var/log/Xorg.0.log
```
Thanks.  Yea I thought about just deleting my xorg.conf file but I was afraid that would render my X useless.  Lesson learned.

---

