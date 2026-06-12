---
title: "creating a wireless network"
date: 2010-03-02
forum: General Help
---

### Post by LeadHop on 2010-03-02
strange problem with ubuntu here.

I have a nokia n900 and trying to use my laptop as a wifi hotspot by creating a wifi network.  the problem is that while the wifi network shows and as connected, it doesn't go through - ie the bars show that the device is connected, but I get the "address not found" sign.  this is true of my other laptop.  help?  thanks!

---

### Post by mikewhatever on 2010-03-02
This is most probably a DNS resolution issue. It's easy to verify by pinging something like google.

ping -c4 74.125.39.104

vs 

ping c-4 google.com

When creating your network, make sure you enter your router's gateway into the DNS field.

---

