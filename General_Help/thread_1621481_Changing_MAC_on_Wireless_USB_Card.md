---
title: "Changing MAC on Wireless USB Card?"
date: 2010-11-14
forum: General Help
---

### Post by Jilles8 on 2010-11-14
Hello everyone!

I just moved from win7 to ubuntu,
besides some changes like the close and minimize on the left side of a programm, I must say
I really love ubuntu!

Now, on windows7 I was able to change my mac address using SMAC, but
I have no clue how on linux.

I used google but that didn't help me either because all tutorials were about wireless lan cards, and im using an Eminent Wireless USB Adapter

Thanks in advance!!
-Jilles8

---

### Post by 0xParse on 2010-11-14
There is a package called "macchanger".  You can get it in Synaptic, or use the console.
In the console install it by using:
  sudo apt-get install macchanger

To change your address run it like this:
  macchanger -m 00:11:22:33:44:55

---

