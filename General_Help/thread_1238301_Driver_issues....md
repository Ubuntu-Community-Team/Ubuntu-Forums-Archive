---
title: "Driver issues..."
date: 2009-08-12
forum: General Help
---

### Post by NH2G on 2009-08-12
I own a Compaq Presario M2000 Notebook Computer and I have recently installed Ubuntu 9.04 on it along side Windows XP.  I have done a fresh install one more time this morning and I know that to activate my Broadcom Wireless driver I must: get all of the security updates, open terminal and type "sudo apt-get update" and then reload the Synaptic Package Manager with the new updates, the problem is that I have beenusing a Linksys USB wireless device and when I attempt to activate my Broadcom wireless driver, the computer reads and installs the driver, but it does not actually work, would this be any different if I were to use an ethernet connection?
 
      Any help would be appreciated.

---

### Post by fennec_fox on 2009-08-12
Do you mean it reads and installs the driver for the linksys usb adapter instead of the normal wireless card? If so then a wired ethernet connection would probably take care of it. If you take out the usb one it should detect the internal one assuming you have a wired connection.

That doesn't necessarily mean it will detect it or work but, I get the idea you're saying it's always detecting the usb adapter instead of the internal one.

---

### Post by synapsys on 2009-08-12
```
sudo apt-get install b43-fwcutter
```

---

