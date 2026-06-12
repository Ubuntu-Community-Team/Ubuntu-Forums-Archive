---
title: "Ubuntu from USB but wifi disabled"
date: 2011-03-21
forum: General Help
---

### Post by k94382 on 2011-03-21
I loaded Ubuntu 10.10 on a USB stick and when everything is loaded and I try to connect to a network, the notice I get is 

```
wireless is disabled
```

[ATTACH]186774[/ATTACH]

for my internal wifi adapter and USB adapter. I remember being able to use them in the past with a fresh install of Ubuntu on the same USB stick. What am I missing?

Thanks,

---

### Post by 5149.5 on 2011-03-21
Open terminal and enter : nm-tool. Paste the results in a post.

---

### Post by Bucky Ball on 2011-03-21
Does the wired work? Try plugging a cable in, get your updates, and see if that provides appropriate drivers or firmware for your devices. You may have something missing with a fresh install.

---

### Post by k94382 on 2011-03-22
> **5149.5 said:**
> Open terminal and enter : nm-tool. Paste the results in a post.

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:E0:91:22:D4:44

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        00:1F:3B:C7:01:9B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        00:C0:CA:3F:BD:A7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



```

---

### Post by k94382 on 2011-03-23
So any suggestions on what I can do now? I do not have access to cable internet since I use the wireless campus network but I am able to get remote desktop working using a crossover ethernet cable and a second laptop.

---

### Post by wojox on 2011-03-24
> **k94382 said:**
> So any suggestions on what I can do now? I do not have access to cable internet since I use the wireless campus network but I am able to get remote desktop working using a crossover ethernet cable and a second laptop.

Then you need to download the wireless driver onto your usb stick.

---

### Post by k94382 on 2011-03-24
According to the output I posted, isn't the driver already available?

---

