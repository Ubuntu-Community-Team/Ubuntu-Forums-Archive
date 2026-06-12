---
title: "epic wifi fail"
date: 2009-10-29
forum: General Help
---

### Post by RikerE on 2009-10-29
Ok, this is going to drive me insane! Personally, I love Ubuntu and am fairly decent on it, yet nothing I know of nor any googling is fixing this illogical challenge...

I just did a clean install of 9.10, disk checks out, the install was rough (tasksel didn't work, note to devs: fix tasksel please) so its just about as empty of an install as I think is possible...

Well, during the install procedure, it had an error configuring the networking, I just left it be cause that being my second run I didn't plan on playing with that...

Eth0 didn't work out box (but it now works) however, reguardless of what I've done, wifi will not when it actually ran by default in 9.04 and with drivers in all previous releases...

Network tools states "The interface does not exist" which just perplexes me as the driver manager found it...

HELP!

PC:
Dell Inspiron 1501
AMD Athlon 64 X2
Ubuntu Studio 64bit

---

### Post by RikerE on 2009-10-30
Yea for IRC!

Problem's fixed, turns out that for some reason, the network manager wasn't installed...

sudo apt-get gnome-network-manager

---

