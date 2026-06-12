---
title: "After hibernating; networking disabled?"
date: 2011-04-03
forum: General Help
---

### Post by laugh1 on 2011-04-03
I've tried clicking "enable networking" but nothing happens and I tried using these codes in terminal as well:
sudo gedit /etc/network/interfaces
sudo /etc/init.d/networking restart

but nothing happens to the connection. A restart fixes the issue, but how can I fix it..?
edit:
I have discovered that if I go to "Lock screen" then close my laptop screen there is no network issues. Temp solution found!

---

### Post by laugh1 on 2011-04-03
Bump.

---

### Post by securitymeddler on 2011-04-03
Hey dude, 

I had something similar with an older computer not too long ago. I don't remember the make and model of my NIC but I ended up picking up a used $4 Intel network card off ebay and never looked back. 

What if the make/model of the network card you are using? open driver or closed?

---

### Post by matt_symes on 2011-04-03
Hi

Is this a wired or wireless connection ?

Please post the output of (case sensitive)

```
lspci -nnk | grep -A3 Network
``` 

Kind regards

---

### Post by laugh1 on 2011-04-03
It is wireless and:

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8181]
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci

```

---

### Post by matt_symes on 2011-04-03
Hi

I am a bit confused. Can you elaborate a bit more on what is disabled. Is it nm_applet or is nm_applet enabled but you can't connect to a network.

Assuming it's the latter, after coming out of hibernation could you post the output of 

```
ifconfig
iwconfig
```

Anyway, that said i will go out on a limb and suggest something to try.

Try unloading and reloading the kernel module after thawing from hibernation.

Open a terminal and type..

```
sudo modprobe -r r8192se_pci
sudo modprobe r8192se_pci
```

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by laugh1 on 2011-04-03
I have discovered that if I go to "Lock screen" then close my laptop screen there is no network issues. Temp solution found!

---

