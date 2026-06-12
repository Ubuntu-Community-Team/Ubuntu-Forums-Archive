---
title: "inxi - what do you think about it?"
date: 2010-11-09
forum: General Help
---

### Post by TBABill on 2010-11-09
I installed Mint 10 last night because I couldn't find my Ubuntu 10.10 DVD. I decided to try to overcome my inability to connect wirelessly on 10.10 with my Ralink RT2860, which ALWAYS connects out of the box on any distro I try. So I found the answer after I installed the OS on a separate partition from my 10.04 partition. But I found the answer on the Mint forums and followed a unique step to identify the card and driver as ```
inxi -N
```
 
So I booted back into my Ubuntu partition to try it out and realized it was unique to Mint, which sent me Googling. I found more info on the script that is added to Mint and Antix and will soon be used in Arch. More info [http://code.google.com/p/inxi/](http://code.google.com/p/inxi/)
 
Wouldn't it be great to have it in Ubuntu since so many people have wireless issues and are constantly being walked through how to identify their wireless device, then how to fix it? Giving such a simple to remember code to a new or less experienced user would give them a single output of exactly what they are needing. Other codes (lspci, for example) give so much detail that most people simply cut and paste and wait for someone to interpret the output. This would narrow the output down to just the necessities.
 
There's a .deb to install it and I plan to give that a shot in my 10.04 partition tonight. Any thoughts?

---

