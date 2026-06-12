---
title: "Azureus doesn't work"
date: 2006-02-25
forum: General Help
---

### Post by Mirrorball on 2006-02-25
I've installed Azureus 2.4 but it's not working. I turned off the firewall with firestarter but torrents stay red or blue, and nothing is downloaded or uploaded. What puzzles me is that the same program version and configuration work on Gentoo, with a firewall running. Does anyone know what could be wrong? NAT is OK, DHT firewalled (I can't fix this either, but it doesn't seem to be a problem on Gentoo).

---

### Post by rudiz on 2006-02-25
Enable the Bittirrent port in ur firewall.

---

### Post by Mirrorball on 2006-02-25
My firewall wasn't even running.

---

### Post by skinnyfat on 2006-02-25
try reading [this thread]("http://ubuntuforums.org/showthread.php?p=768680"):

I had the same issue

Good luck

---

### Post by Mirrorball on 2006-02-26
I didn't use Automatix to install Azureus, I just installed Sun Java 1.5 and extracted Azureus_2.4.0.0_linux.tar.bz2 to /opt according to [these instructions](http://easylinux.info/wiki/Ubuntu). Do I need to update the SWT library as well?

---

### Post by Mirrorball on 2006-02-26
I installed Blackdown Java 1.4 and now Azureus works.

---

### Post by Sidha on 2006-02-26
it seems to me that firewaller doesn't unblock the DHT ports

I have installed Azureus and Java the simple way (just downloading it and then put it somewhere) .. works just wonderful ... if you don't forget to edit the azureus script (/opt/azureus/azureus) and change the first two lines to valid values.

but NOT with the firewall enabled?? at least the DHT ports don't open  :-k

---

