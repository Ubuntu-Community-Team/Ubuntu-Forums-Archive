---
title: "Ubuntu freezes after reinstallation"
date: 2011-04-01
forum: General Help
---

### Post by Shaddow89 on 2011-04-01
Hi,

I just got a new SSD and installed Ubuntu on it. Since the installation I am encountering regular freezes. By now, I cannot point out any regularities. I still can move the mouse, but thats it. I cannot access the terminal, no key comination works. I can only reboot by turning off the power...

Since I am quite new to problem handling on Ubuntu (til now everything used to work fine ;) ), I am not quite sure, what information you need, to give me hints.

But I at least can provide some hard- and software information:

Laptop type: Thinkpad W510
RAM: 12GB 
OS: Ubuntu 10.10

I hope you can help me
thanks in advance

---

### Post by An Sanct on 2011-04-01
When booting up, hold down the **Shift** key, this will bring up GRUB menu. 
There you can select "*Ubuntu, with Linux 2.6.X.YY (***recovery mode***)*"

First try the "Clean" menu entry (not necessary), then try "DPKG", This will run the updates (if any)

If there are no updates, you can still try "Failsafe X", which will bring you to your desktop in safe mode.

PS. I use Ubuntu on SSD, since Hardy and it was never a problem, SSD to the system is just a "normal disk", but fast :). If the problems are hardware related, its elsewhere.

---

