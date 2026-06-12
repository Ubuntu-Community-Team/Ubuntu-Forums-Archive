---
title: "GeForce 2 problems!"
date: 2006-05-09
forum: General Help
---

### Post by rkoep on 2006-05-09
Hi, I've got a problem installing my new (old though) graphics card, a geforce 2 mx, a 32 mb agp card. When i just plug it in instead of my standard pci card, xServe wont start up anymore, but it just gives me a blue screen with the error message, and after that I end up in the terminal. I guess i have to install some drivers or something, but i don't know how ;) 
Please help me! :)

---

### Post by Duke_Of_Earl on 2006-05-09
Whats the error message?

:)

---

### Post by Omnios on 2006-05-09
Log into to terminal and type 
```
sudo dpkg-reconfigure xserver-xorg
```
 This will take you into a turtle like graphics graphical xorg config where you can set up your new vid card.

---

### Post by rkoep on 2006-05-09
I have tried your solution, but unfortunately it didn't work. I did manage to configure my old graphics card to work again, after i put it back. I read that it could help to use the vesa drivers in the xserver reconfigure, because they tend to work better (and with more cards) than the nv drivers, but that didn't really work either... Any ideas on fixing this?

---

### Post by Omnios on 2006-05-09
It might be a problem with detecting the slot that the card is installed to. I have heard of this before. I dont know much about it but when you do reconfigure you can type the slot where the hardware is installed.

---

### Post by gRiMgRaVy014 on 2006-05-09
Yes it the question asking for the PCI bus info, for example, my bus info is PCI:1:10:0
 You might be able to figure it out with the lspci command.

---

### Post by rkoep on 2006-05-13
Hey guys, I was zuite busy the last couple of days, but i solved my problem! I found another videocard (I've got computer parts all over my house :p ), and that one did work using the reconfigure xserver command. much thanks for the help!

---

