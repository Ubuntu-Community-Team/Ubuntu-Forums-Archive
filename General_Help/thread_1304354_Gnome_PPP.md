---
title: "Gnome PPP"
date: 2009-10-29
forum: General Help
---

### Post by tempus on 2009-10-29
Does this still work in 9.01? Have they removed all dial-up modem support in this release? My modem worked perfectly in 9.04 so I am wondering. the modem is a USR usb.

---

### Post by PorkyPie on 2009-10-29
> **tempus said:**
> Does this still work in 9.01? Have they removed all dial-up modem support in this release? My modem worked perfectly in 9.04 so I am wondering. the modem is a USR usb.

If you're talking about gnome-ppp, you can download it from the repos still.

---

### Post by tempus on 2009-10-29
> **PorkyPie said:**
> If you're talking about gnome-ppp, you can download it from the repos still.

I did and it seems to not detect the modem which, in 9.04 it did.

---

### Post by Sealbhach on 2009-10-29
Does the modem show up when you run lsusb?

Just open a terminal and run the command

```
lsusb
```

I would have thought you could configure your connection using Network Manager, without needing to use Gnome-PPP.

.

---

### Post by tempus on 2009-10-29
> **Sealbhach said:**
> Does the modem show up when you run lsusb?

Just open a terminal and run the command

```
lsusb
```

I would have thought you could configure your connection using Network Manager, without needing to use Gnome-PPP.

.

I will try exactly as you have suggested.

---

### Post by tempus on 2009-10-29
> **Sealbhach said:**
> Does the modem show up when you run lsusb?

Just open a terminal and run the command

```
lsusb
```

I would have thought you could configure your connection using Network Manager, without needing to use Gnome-PPP.

.

yes the modem is detected with lsusb. However in gnomePPP is is not.

---

### Post by tempus on 2009-10-29
> **tempus said:**
> yes the modem is detected with lsusb. However in gnomePPP is is not.


Still not detecting the modem in gnomeppp which is the program i want to use to dial out on. You may be asking why I am fussing a dial up but when i visit my family in the country all they have is dial up.   :popcorn:

---

### Post by Sealbhach on 2009-10-30
> **tempus said:**
> yes the modem is detected with lsusb. However in gnomePPP is is not.

OK, copy and paste the output from lsusb here, so that we know the exact type of modem it is.

.

---

### Post by tempus on 2009-10-30
> **Sealbhach said:**
> OK, copy and paste the output from lsusb here, so that we know the exact type of modem it is.

.

will do that very soon. But in the readout I did tsee the modem listed as a USR usb type modem. So somewhere in ubuntu something is not communicating...don't know what though. :popcorn:

---

### Post by Sealbhach on 2009-10-30
> **tempus said:**
> will do that very soon. But in the readout I did tsee the modem listed as a USR usb type modem. So somewhere in ubuntu something is not communicating...don't know what though. :popcorn:

Something changed in the kernel, I guess, it happens sometimes. If I were you I would create a bug report on Launchpad. See here:

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

It's the quickest way to get something done about it.

.

---

### Post by tempus on 2009-10-31
> **Sealbhach said:**
> Something changed in the kernel, I guess, it happens sometimes. If I were you I would create a bug report on Launchpad. See here:

[https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net](https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net)

It's the quickest way to get something done about it.

.

Ok. Thanks for the tip.

---

### Post by tempus on 2009-11-07
i may need to go back to version 9.04 if I hope to have a working modem. How did they manage to destroy this version's ability to connect with a dial-up modem? I don't really want to go back if it's not necessary. Help!:popcorn::popcorn:

---

