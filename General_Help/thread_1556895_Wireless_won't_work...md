---
title: "Wireless won't work.."
date: 2010-08-20
forum: General Help
---

### Post by OpressedCalamity on 2010-08-20
I am relatively  new to linux, and I am dual booting Ubuntu 10.4 (Lucid Lnyx), and I do love it, but my wireless won't work and a wired connection just is not a option. I have tried using a Wireless usb adapter class N, that didin't work so I tried my only other wireless adapter a Dell wireless 1450 Wireless USB adapter.
Windows just is not a option.
Thanks in advanced for any help!

---

### Post by JBAlaska on 2010-08-20
For the **Dell wireless 1450 Wireless USB adapter**

If you can connect with a wired connection, run this from a terminal:
```
sudo apt-get install linux-firmware-nonfree
```

If you have no inet access with this computer, you can download the [deb file](https://edge.launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8) on another box and use a flash drive or cd to transfer and run it on your machine.

---

### Post by OpressedCalamity on 2010-08-20
> **JBAlaska said:**
> For the **Dell wireless 1450 Wireless USB adapter**

If you can connect with a wired connection, run this from a terminal:
```
sudo apt-get install linux-firmware-nonfree
```

If you have no inet access with this computer, you can download the [deb file](https://edge.launchpad.net/ubuntu/lucid/i386/linux-firmware-nonfree/1.8) on another box and use a flash drive or cd to transfer and run it on your machine.

Thank you I will give that a try!

---

### Post by OpressedCalamity on 2010-08-20
I love you forever, this worked thanks!!!

---

### Post by Ripfox on 2010-08-20
linux-firmware-nonfree huh? Seems like i missed a lesson...

---

### Post by Ripfox on 2010-08-20
> **Ripfox said:**
> linux-firmware-nonfree huh? Seems like i missed a lesson...

Uh I downloaded tis...total satisfaktonnnnnnnn

---

