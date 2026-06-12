---
title: "Dual Boot on AMD processor"
date: 2012-08-22
forum: General Help
---

### Post by vikrantalmelkar on 2012-08-22
Hi Team,
 
I have just got a new Toshiba Laptop, but it has a AMD processor. I tried installing Ubuntu on it but it freezes as soon as the wired internet connection is taken out and wire less modem kicks in.
 
can someone please help me solve this problem as I hate using Windows.:mad:
 
All your help is really appreciated
 
Thanks
Vikrant

---

### Post by mastablasta on 2012-08-22
your problem has nothing to do with AMD processor but obviously with wi-fi.
 
lspci 
 
command should tell you what chip it is. post the output here so people can troubleshoot.

---

### Post by vikrantalmelkar on 2012-08-22
Hi Mastablasta,

would the following help:

CPU	AMD E450 (Dual Core 1.65GHz, 1066MHz FSB, 1MB L2 Cache)
Chipset	AMD Hudson M1

please let me know how I can overcome this 

Thanks for all your help

Vikrant

---

### Post by vikrantalmelkar on 2012-08-23
Hi Team,
 
can someone please help me with the issue with my laptop wifi
 
Thanks
Vikrant

---

### Post by steeldriver on 2012-08-23
Like mastablasta said, you need to provide some info about the wireless chipset (_not _the CPU chipset)

There are a number of different commands you can run in a terminal to get this information, e.g.

```
sudo lshw -C network
``````
lspci -nnv | grep -A2 -E '\[(0200|0280)\]'
```If you post back with the output of those commands we can try to help you

---

