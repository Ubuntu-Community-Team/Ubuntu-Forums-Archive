---
title: "mad wifi"
date: 2009-09-22
forum: General Help
---

### Post by geogur on 2009-09-22
i really need to get my wifi working on my destop .I bought a card installed it and can not get it to work . a friend told me about mad wifi but the source forge repository is obsulete . i have tried and failed to download and install mad wifi . Is it possible to get wifi working on a ubuntu desktop? if so how can i do this

---

### Post by baseface on 2009-09-22
u tried ndiswrapper?
what card did you buy?
probably should have made sure it would work before you bought it.

---

### Post by geogur on 2009-09-22
I did ask at computor canada for a card that works and was sold on the linksystem gnet . but can`t get it to work . the install disk has vista and xp drivers only and there support says i am on my own ?

---

### Post by geogur on 2009-09-22
I did try wicd and ndiswrapper both times I lost my lanline I even tried a fresh install of off ubuntu9.04 disc hoping there is some code there that will install when the new hardware was detected but no such luck

---

### Post by geogur on 2009-09-22
I really need to go to work now so i will check back latter when i return home

---

### Post by NullHead on 2009-09-22
Chances are, if you're running Ubuntu 9.04, there is a driver for your card available in the repository. Check the restricted drivers manager in System>Administration>Hardware Drivers. You'll find drivers in there for your video card, and probably your wifi card. You'll need an internet connection in order to use that Hardware Drivers program.

Lemme know what you see in there.

---

### Post by geogur on 2009-09-23
okay i can run a lan line over to my ubuntu box yes i am running ubuntu 9.04 that would be great if it is already there . thats only because i have not got a good understanding of how to download linux files and instaling them or compiling the kernel ? i will try this saterday for my ubuntun pc is 100 kilometers away my zandros eeepc no problems i am using free internet to make this post i hope the next post will be solved . lets see what happens saterday . thanks for your advice .

---

### Post by geogur on 2009-09-23
i have restricted drivers installed for my dual head 17" 20" lcd displayes . so iwas there already does  this mean i have already have downloaded the drivers now i need to find and install them .

---

### Post by P4man on 2009-09-23
It might help if you posted what wireless network card you have. If you're not sure, open a terminal and type:

```
lsusb
```

(if its a USB dongle)

```
lspci
```

(if its an internal card)

copy paste the output here.

---

### Post by 3rdalbum on 2009-09-23
Wireless cards are not all standard; they all use different chipsets. Many wireless chipsets work out-of-the-box with Ubuntu, but it seems like yours doesn't.

If you want to return that card and get one that works out-of-the-box with Ubuntu, you should do some research online for what cards are available at the store and which ones are reported to work out-of-the-box.

Alternatively, Linux Emporium sells one that they guarantee will work.

---

