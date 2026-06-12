---
title: "Installation problem"
date: 2011-07-17
forum: General Help
---

### Post by ItsMisterRed on 2011-07-17
So I've been trying to install ubuntu for two days now without success, the trial version works fine, everything works actually, internet, data access, applications, everything. But when I finally install it, nothing works after the first login, everything I start takes far longer to load, and when it's fully loaded, it closes immediately, I have this problem with everything, calculator, data access, firefox, etc.....

Does anyone know what might be wrong? 
I tried installing linux mint instead and the same problem happened.

I'm trying to install ubuntu 11.04 via usb and my specs are :

AMD Athlon II X2 250
2 X 2G RAM 1333mhz
Motherboard MSI GF615M-P33 V2
Hard drive sata II 500GO 16mo 7200rpm

---

### Post by shashanksingh on 2011-07-17
Weird, if the "try ubuntu" option is working fine.

I can't give you the solution, but I know people can if you could help them by attaching these outputs from the terminal:

1. sudo lshw
2. dmesg

---

### Post by ItsMisterRed on 2011-07-17
Thanks.

Here's what I get with sudo lshw : [http://pastebin.com/dzft2AW1](http://pastebin.com/dzft2AW1)
And here's what I get with dmseg : [http://pastebin.com/CTZkMHsk](http://pastebin.com/CTZkMHsk)

---

### Post by shashanksingh on 2011-07-17
> **ItsMisterRed said:**
> Thanks.

Here's what I get with sudo lshw : [http://pastebin.com/dzft2AW1](http://pastebin.com/dzft2AW1)
And here's what I get with dmseg : [http://pastebin.com/CTZkMHsk](http://pastebin.com/CTZkMHsk)

Do one more thing.
Also paste the dmesg while  you are running it from the live Cd
The differences in the two may give hints.

---

### Post by ItsMisterRed on 2011-07-17
Both actually are from the livecd, I can't access the terminal once ubuntu is installed.

---

### Post by ItsMisterRed on 2011-07-17
Bump.

---

### Post by ItsMisterRed on 2011-07-17
Is it possible my hardware is incompatible with linux?

---

