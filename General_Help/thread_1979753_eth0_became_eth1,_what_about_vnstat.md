---
title: "eth0 became eth1, what about vnstat?"
date: 2012-05-14
forum: General Help
---

### Post by MichaelGld on 2012-05-14
Ok, so I got my replacement motherboard - the old one was locking up constantly, this one seems good so far. It's the exact same model, but I did put in a better cpu (FX-4100 Quad Core).  My conky shows no network traffic because it was listening to eth0, which was where all the action was on my old board. Only has the one ethernet port. But the new board is going through eth1.

The thing is, vnstat needs to be changed somehow to reflect the new port, because it doesn't seem to be recording any traffic. I've looked at the man pages and I'll be darned if I can figure it out. Can anyone help me out?

---

### Post by stinkeye on 2012-05-14
Create a new database for eth1
```
sudo vnstat -u -i eth1
```

---

### Post by roelforg on 2012-05-14
In /etc/udev/udev.d there should be a file named 70-persistent-net.rules
Put a # in front of every line that doesn't have one already and reboot.
The numbering for nic's is reset and you should have eth0.

---

### Post by MichaelGld on 2012-05-14
The directory structure on my system (11.04) is a little different. Instead of a folder called udev.d, I have a folder called rules.d, but it has the same file in it that you mentioned. I did as you said and it's all working as it should. Thanks for the help.


> **roelforg said:**
> In /etc/udev/udev.d there should be a file named 70-persistent-net.rules
Put a # in front of every line that doesn't have one already and reboot.
The numbering for nic's is reset and you should have eth0.

---

### Post by roelforg on 2012-05-14
> **MichaelGld said:**
> The directory structure on my system (11.04) is a little different. Instead of a folder called udev.d, I have a folder called rules.d, but it has the same file in it that you mentioned. I did as you said and it's all working as it should. Thanks for the help.

Yeah sorry, i typed that from my phone and made a mistake.
I meant rules.d (but hey, you figured it out so who cares).
I move hd's around a lot and some stuff has eth0/1/2 hardcoded so it's standard procedure for me to erase that file (though i usually just manually edit it, but for the avg. user erasing is fine).

---

