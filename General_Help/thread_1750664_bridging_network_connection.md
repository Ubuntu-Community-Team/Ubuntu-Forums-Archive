---
title: "bridging network connection"
date: 2011-05-05
forum: General Help
---

### Post by Pwntastic on 2011-05-05
First of all I have a Ethernet cable from the wall to my desktop then I have a Ethernet cable from my desktop to my laptop. Before I did a fresh install of Ubuntu 11.04 I was using Ubuntu 10.10 and I found a tutorial to make this network bridge work by changing settings in the Devices - Network Tools. I need to make  this bridge work again and i totally forgot how and I can't find the tutorial.

---

### Post by recce_ on 2011-05-26
> First of all I have a Ethernet cable from the wall to my desktop then I  have a Ethernet cable from my desktop to my laptop. Before I did a fresh  install of Ubuntu 11.04 I was using Ubuntu 10.10 and I found a tutorial  to make this network bridge work by changing settings in the Devices -  Network Tools. I need to make  this bridge work again and i totally  forgot how and I can't find the tutorial.This has been solved but for your convieance:

Install bridge-utils
```

sudo apt-get bridge-utils

```Activate your bridged connection; access your interfaces:
```

sudo nano /etc/networking/interfaces

```
Add:
```

iface br0 inet dhcp
     bridge_ports all 

```Done.

Good luck.

-Recce

---

### Post by ksaul on 2011-10-22
> **recce_ said:**
> This has been solved but for your convieance:

Install bridge-utils
```

sudo apt-get bridge-utils

```Activate your bridged connection; access your interfaces:
```

sudo nano /etc/networking/interfaces

```
Add:
```

iface br0 inet dhcp
     bridge_ports all 

```Done.

Good luck.

-Recce

I tried this but did not have any luck.. 
1) you need to fix step 1:   "sudo apt-get install bridge-utils"
2) When I did step 2- and tried to save, (it opened fine and I was able to add the lines to it -- although the file itself was empty) it said the file did not exist.
 I tried to access the folder itself (cd /etc/networking/) and said it doesnt exist.
3) Did not bridge a connection =(

HALP PLEASE!!


edit: I found the file for step 2 in     /etc/**network**/interfaces

---

