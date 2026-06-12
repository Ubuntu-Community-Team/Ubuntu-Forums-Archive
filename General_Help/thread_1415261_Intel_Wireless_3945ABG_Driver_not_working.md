---
title: "Intel Wireless 3945ABG Driver not working???"
date: 2010-02-24
forum: General Help
---

### Post by tarrbros on 2010-02-24
So how would i connect to the Internet in Ubuntu with the Intell 3945AGB driver? I can't find anyway to do this. I am brand new to Linux and i don't know how to do anything. Can anyone help me? Thanks!

---

### Post by tarrbros on 2010-02-24
BUMP! No one?

---

### Post by tarrbros on 2010-02-24
somebody?

---

### Post by drink_stir on 2010-02-25
well... mine worked right out of the box. iwl4965. idk whats up with urs. have u tried to start networking??  ```
sudo /etc/init.d/*networking start*
```

---

### Post by guren on 2010-02-25
I think we have the same wireless card..

can you try
```

lsmod | grep iwl3945

```

---

### Post by RegUB on 2010-02-25
According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) it should work out of the box, though mine didn't when running from the live CD.

---

### Post by tarrbros on 2010-02-25
ill try it

---

### Post by drink_stir on 2010-02-25
mine worked from live cd.  if it didnt i think i woulda been to scared to come to linux.. eh not really. but anyway any live cd ive tried has worked with my card. im not sure whats up with yours.

---

### Post by guren on 2010-02-25
Sometimes I have to check/uncheck "Enable Wireless" in NetworkManager applet on my gnome panel. This usually happens when I accidentally switch off the wifi switch of my laptop.

---

### Post by Hausi on 2010-02-26
funny, my iwl3945 was working with kernel 2.6.32.9 and stopped working with 2.6.33
with th older kernel (2.6.32.9) i see an entry in dmesg like 'requesting firmware' while with 2.6.33 there is no such such message. the module loads but does not request firmware....
strange:rolleyes:
_hans

---

