---
title: "Internet doesn't work on Ubuntu 10.04"
date: 2012-01-16
forum: General Help
---

### Post by rickyLOLZ on 2012-01-16
Hello!
Yesterday, i installed Ubuntu and dual booted it with Windows 7, but the internet works on Windows7 but doesn't work on Ubuntu.

[maybe this has something to do with Wubi 10.04 because i installed Ubuntu using it.]

When i click the internet network manager on Windows7, there appears a bunch of networks including my internet network, but on Ubuntu, when i click it's internet network manager, no networks appear.

Thanks for any help,
RickyLOLZ.

---

### Post by WasMeHere on 2012-01-16
Hi RickyLOLZ,

Wired internet works out of the box (almost always). But there are issues with several wireless LAN chips and cards.

Have a look at the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Have fun finding out about Ubuntu :-)
Olle

---

### Post by rickyLOLZ on 2012-01-16
> **Olle Wiklund said:**
> Hi RickyLOLZ,

Wired internet works out of the box (almost always). But there are issues with several wireless LAN chips and cards.

Have a look at the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Have fun finding out about Ubuntu :-)
Olle

Thanks! I'll try.

---

### Post by rickyLOLZ on 2012-01-16
> **Olle Wiklund said:**
> Hi RickyLOLZ,

Wired internet works out of the box (almost always). But there are issues with several wireless LAN chips and cards.

Have a look at the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Have fun finding out about Ubuntu :-)
Olle

...i forgot here in Portugal we don't have any Ubuntu thing on the stores, so what do i do? I read it.

---

### Post by WasMeHere on 2012-01-16
> **rickyLOLZ said:**
> ...i forgot here in Portugal we don't have any Ubuntu thing on the stores, so what do i do? I read it.
The list shows standard commercial wifi equipment (mainly for Windows). Some of these standard equipment also work with Ubuntu. If you cannot find it in a store, maybe you can get it via an internet store, or ask some local guy to get it for you.

---

### Post by WasMeHere on 2012-01-16
It is worth trying the newest Ubuntu (or Kubuntu, Xubuntu, Lubuntu) version **11.10**, because it has built-in support for several new wifi devices. You can test it from a live CD or USB drive without installing until you know that it works.

---

### Post by rickyLOLZ on 2012-01-16
> **Olle Wiklund said:**
> It is worth trying the newest Ubuntu (or Kubuntu, Xubuntu, Lubuntu) version **11.10**, because it has built-in support for several new wifi devices. You can test it from a live CD or USB drive without installing until you know that it works.

Ok! Thanks.

---

### Post by Tony Flury on 2012-01-16
Can you open a terminal and post the results of the following commands : 
```

lspci

```
and 
```

sudo lshw -C Network

```
This might help us track down the issue with you wireless card in 10.04

---

