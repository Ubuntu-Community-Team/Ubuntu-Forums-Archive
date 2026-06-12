---
title: "How to force NIC to 10Mbit Full Duplex?"
date: 2010-06-08
forum: General Help
---

### Post by haecceitas on 2010-06-08
I have a modem that is only compatible with NIC's using 10Mbit Full Duplex.
If I have a NIC configured to use 100Mbit Full Duplex, the modem loses connection with the computer frequently.

How do I configure my NIC in Ubuntu to use 10Mbit Full Duplex instead of 100Mbit?

Thanks in advance!

---

### Post by gmargo on 2010-06-08
Have a look at the **mii-tool** man page from the **net-tools** package.  It has some stuff about setting the line speed and duplexness.  I don't know offhand how to make it automatic though.  (You very likely want to use half-duplex at 10Mbps but you should be able to try every possibility.)

---

### Post by doas777 on 2010-06-08
I generally use ethtool (which uses miitool I believe) to set em,. 

[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

---

### Post by haecceitas on 2010-06-08
Thank you very much! That solved it.

---

