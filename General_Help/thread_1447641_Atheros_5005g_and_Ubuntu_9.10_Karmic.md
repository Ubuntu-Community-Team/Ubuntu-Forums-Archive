---
title: "Atheros 5005g and Ubuntu 9.10 Karmic"
date: 2010-04-05
forum: General Help
---

### Post by Heyman on 2010-04-05
Hi All,

I did a fresh install of 9.10 on my old war-torn Toshiba Laptop before the weekend, and as a relative noob to Linux, I've been pleasantly surprised so far with how quick and easy everything is.

However, I did hit an issue with my Atheros built-in wireless card.  It seems that the bundled driver (ath5k) doesn't do the job particularly well and unfortunately I couldn't get a reliable connection to my Wireless Router (WEP).  Having done a search of the forums I can see that this has historically always been an issue but couldn't find anything really for issues with the current 9.10 release.

After a lot of messing about (largely due to me being a noob!) I've managed to sort it so thought I would post what I did here to help anyone else who is encountering the same problems -

1.  Uninstalled Network Manager and replaced with WICD (didn't immediately solve the problem but might have ultimately helped).

2.  Unloaded and blacklisted the 'ath5k' driver.

3.  Went to the madwifi website and downloaded the latest drivers (being sure to go for the snapshot for kernels newer than 2.6.2.5 on the front page!). 

4.  Followed the instructions in the readme files within the madwifi driver package to compile and install the drivers.

5.  Used modprobe to load the newly installed ath_pci driver.

Following all of that, I've now got a reliable wi-fi connection!  Sorry for the lack of detail above but all the info for each step is right here in the forums, which is where I got it!

Not sure if there is an easier way to do this?  Hope it helps someone in any case.

H.

---

### Post by nothingspecial on 2010-04-05
If you type ```
sudo nano /etc/modules
```

and add the line ```
ath_pci
``` to the file

and type ```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
``` and put a # infront of the line

```
blacklist ath_pci
```

and then do ```
sudo nano /etc/modprobe.d/blacklist.conf
```

and add the line ```
ath5k
``` this will happen automatically. 

To save in nano press Ctrl+O

To close nano press Ctrl+X

---

