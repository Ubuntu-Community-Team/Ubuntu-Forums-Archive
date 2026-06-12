---
title: "Pavilion dv6"
date: 2011-01-21
forum: General Help
---

### Post by Spyderkid on 2011-01-21
does anyone know if the Wireless works on the new Pavilion dv6 laptop. thanks.

---

### Post by Cakebatter on 2011-01-21
I am using an HP Pavilion DV7 and the wireless networking worked right out of the box!

The only issue I have is that everytime I boot the laptop, I have to tell it to connect to the router.  It's just a matter of clicking on the icon at the top of the desktop and it shows the networks near me.  I then choose my router and it connects perfect.

Ubuntu 10.10

---

### Post by corncob on 2011-01-21
> **Cakebatter said:**
> I am using an HP Pavilion DV7 and the wireless networking worked right out of the box!

The only issue I have is that everytime I boot the laptop, I have to tell it to connect to the router.  It's just a matter of clicking on the icon at the top of the desktop and it shows the networks near me.  I then choose my router and it connects perfect.

Ubuntu 10.10

I had a similar HP and it too worked fine.
Right-click the network icon on the panel and select Edit Connections...  Go to the Wireless Tab and highlight your network, then click the Edit button.  Finally, check the box that says 'Connect Automatically.

---

### Post by Spyderkid on 2011-01-22
Okay thanks!

---

### Post by Spr0k3t on 2011-01-22
> **Spyderkid said:**
> does anyone know if the Wireless works on the new Pavilion dv6 laptop. thanks.

So far, I've seen five different wireless cards in the DV6 from HP.  I think four of them are compatible where one of them is using RaLinks new .11n structure (I believe it's been added to the latest .37 of the kernel).  Of those, two different broadcom (43xx), one Atheros (ath9k) and an intel (ip22k).  Most of them use broadcom though.  You can check your card and driver by using "lspci -v"

---

### Post by royarn on 2011-01-22
My dv6 entertainment laptop with the atheros works great, and setting it up was a no brainer, just click the icon, select my profile, type in key and use.

best Roy

---

### Post by Spyderkid on 2011-01-22
ok thanks again.

Does anything else not work or is it an all go 

(I have Ubuntu on a seperate desktop btw so im not too new to Ubuntu)

---

