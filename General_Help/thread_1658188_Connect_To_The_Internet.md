---
title: "Connect To The Internet?"
date: 2011-01-02
forum: General Help
---

### Post by bustedup277 on 2011-01-02
Can someone help me connect to the internet on Ubuntu? I am using wlan (wireless connection). But you see, I can't connect for some reason. It won't show any networks and there is a ! on the connection sign thing. So I open up to see my drivers and- there are no drivers. Do I need some drivers? How can I download them? Or if not, what do I need to do to connect to the internet?

SPECS
*****
Network Card Info Thingy: Broadcom 4313 802.11b/g/n, Realtek PCIe FE Family Controller
Using: Ubuntu Version 10.04
Original OS: Windows 7

---

### Post by TeoBigusGeekus on 2011-01-02
My sister's netbook had exactly the same problem.
Solved it using [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and the windows drivers.

---

### Post by bustedup277 on 2011-01-02
> **TeoBigusGeekus said:**
> My sister's netbook had exactly the same problem.
Solved it using [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and the windows drivers.

Aight, but do I need CDs to perform this? Because my netbook does not a place to put CDs in.

---

### Post by TeoBigusGeekus on 2011-01-02
No cds needed. It would be helpful though if you had (wired) access to the internet.

---

### Post by ruben_linux on 2011-01-02
i found it:

[http://community.linuxmint.com/tutorial/view/218](http://community.linuxmint.com/tutorial/view/218)
 i think is good

---

### Post by TeoBigusGeekus on 2011-01-02
> **ruben_linux said:**
> i found it:

[http://community.linuxmint.com/tutorial/view/218](http://community.linuxmint.com/tutorial/view/218)
 i think is good

I did try with wl (and bc43, and bc43 legacy)... Very unstable results.
The windows drivers worked the best.

---

### Post by bustedup277 on 2011-01-02
> **TeoBigusGeekus said:**
> I did try with wl (and bc43, and bc43 legacy)... Very unstable results.
The windows drivers worked the best.

The Ndsiwrapper looks quite complicating, is it easy or difficult? How long will it take? There sure is a lot to read. :s

---

