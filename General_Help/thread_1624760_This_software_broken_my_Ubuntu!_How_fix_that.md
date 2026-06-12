---
title: "This software broken my Ubuntu! How fix that?"
date: 2010-11-18
forum: General Help
---

### Post by riksia on 2010-11-18
UBUNTU 10.10

I tried to install sandbox game maker in software center. The installation has stopped. So I tried to install it in Synaptic. There was a  "processing error" and Synaptic started download it again and again.

I restarted my PC and I launched synaptic again. It requires sudo dpkg --configure -a so I did it and the synaptic started download it again. 200Mb

I can't install any software now.

Sorry for my English.

How fix that? Format? :D

---

### Post by elliotn on 2010-11-18
if its broken do this

sudo apt-get install -f

it shall fix it

---

### Post by riksia on 2010-11-18
```
m@m-desktop:~$ sudo apt-get install -f
[sudo] password for m: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

So I did that sudo dpkg --configure -a  but synaptic trying again to download files. And it still repeating.

---

### Post by riksia on 2010-11-18
Yeah! Now synaptic works! I disconnected the internet and I did sudo dpkg --configure -a and it ca'nt download the files so it stopped that! :D

---

### Post by elliotn on 2010-11-18
> **riksia said:**
> Yeah! Now synaptic works! I disconnected the internet and I did sudo dpkg --configure -a and it ca'nt download the files so it stopped that! :D

ok so its solved

---

