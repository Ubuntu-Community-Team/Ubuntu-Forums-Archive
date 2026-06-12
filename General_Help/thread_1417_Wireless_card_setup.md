---
title: "Wireless card setup"
date: 2004-10-20
forum: General Help
---

### Post by wlaver on 2004-10-20
Hi all,
 I have just installed ubuntu (very impressed). One thing though. I cannot seem to get my wireless card configured.

I have a toshiba satellite m30 with a intel pro 2200BG wireless card. Ubuntu has found the hardware and I believe even installed the driver, but I do not know how to configure the card to connect to my wireless network. Curently i'm trying to use the gnome-wireless config applet, but it is telling me that there are no-wireles devices.

Any input would be appreciated.

wl

---

### Post by knappen on 2004-10-21
Can you see ipw2200 when you type 

```

dmesg
```

Try this, it worked for me

```
modprobe ipw2200
modprobe firmware_class

```

Click on Computer, System Configuration, Networking

In there you can edit your setup.

Good luck!

---

