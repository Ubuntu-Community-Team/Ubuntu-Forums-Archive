---
title: "How could I install modem driver using CDROM"
date: 2006-02-09
forum: General Help
---

### Post by Ubuntu_learner on 2006-02-09
Hi folks,
Please advise me on how to install the modem driver I've downloaded from Conexant's Linuxant website. I've downloaded it using WinXP and burned it into my CDROM. I used Synaptic but it says that my CDROM is not a debian disc. What does this mean (i.e., my CDROM not being a Debian disc)?

For your reference the downloaded driver for my D-Link DFM-562iS modem: 

hsfmodem_7.18.00.07full_k2.6.12_9_386_ubuntu_i386.deb

Hope to hear from all of you soon.

Thanks a lot!:)

---

### Post by Greg2 on 2006-02-09
Copy the 'driver .deb' from the CD to your home directory. Then in terminal do:```
sudo dpkg -i hsfmodem_7.18.00.07full_k2.6.12_9_386_ubuntu_i386.deb
```

---

### Post by lance bermudez on 2006-02-09
from terminal cd /cdrom then do the rest with dpkg -i

---

### Post by lance bermudez on 2006-02-09
forgot make sure you are using sudo cd /cdrom and sudo dpkg -i
also if you do not want to keep typing sudo just type sudo su -

---

### Post by Ubuntu_learner on 2006-02-10
Hi Greg2 and Lance,
Many many thanks for your advice!! I have the driver now installed. But it just keeps on dialling for a while then becomes busy. Still not yet connected to the internet using Ubuntu. What do you think is the problem? 
Rgds

---

