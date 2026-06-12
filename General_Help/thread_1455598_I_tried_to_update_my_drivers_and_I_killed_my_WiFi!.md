---
title: "I tried to update my drivers and I killed my WiFi!"
date: 2010-04-16
forum: General Help
---

### Post by ninjaaron on 2010-04-16
I've been having some problems with my Atheros AR9285 wireless card, so I asked some questions, did some searching, etc.

Anyway, I found this page:[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

In Step #1 it says something about downloading the latest stable version from [http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/")

I did. It's compat-wireless-2.6.34-rc4.tar.bz2, or so I believe. I was a little suspicious about this, since I have only have the 2.6.31-20 generic kernel or something like that, but I figured if the tutorial said I should get the latest, who am I to question it? I don't understand the deep ways of the Linux.

So I built, installed, and unloaded the packages, then rebooted. No WiFi anymore. I restarted again. Same thing. Now I'm in Windows trying to get it sorted. Just give me my internet back!!

Thanks,
Aaron

---

### Post by nothingspecial on 2010-04-16
What happens if you type
```

sudo modprobe ath9k
sudo service networking restart
```

---

### Post by ninjaaron on 2010-04-16
> **nothingspecial said:**
> What happens if you type
```

sudo modprobe ath9k
sudo service networking restart
```

I did the modprobe. It said.
```

WARNING: Error inserting pcmcia_core (/lib/modules/2.6.31-20-generic/kernel/drivers/pcmcia/pcmcia_core.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting compat (/lib/modules/2.6.31-20-generic/updates/compat/compat.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-20-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

So, I don't totally know what the deal with the unkown symbol is, but I sure wish my ath9k had been inserted, whatever the heck that means.

I did the other thing (service networking restart) too and it said something about unknown something. I dunno. I guess it's not gonna work until I get the unknown symbols out of my modules, which is not something I feel quite up to.

---

### Post by nothingspecial on 2010-04-16
As a work round, for now, do you have any other kernels to boot into, to at least get back to the state you were in before you started.

---

### Post by ninjaaron on 2010-04-16
Yeah, that seems to be working.

---

### Post by ninjaaron on 2010-04-16
> **nothingspecial said:**
> As a work round, for now, do you have any other kernels to boot into, to at least get back to the state you were in before you started.

That also gave me the idea to reinstall the kernel, the wifi is working again. I'd still like to update my drivers, but I don't know what I did wrong the first time.

---

### Post by nothingspecial on 2010-04-16
It may have been the fact it was built for a different kernel, like you said in your first post.

---

### Post by takamarou on 2010-10-19
Hi, sorry for reviving such an old article. I'm having the exact same problem as the OP, but a kernel reinstall did not help.  

My wifi was originally working when I installed ubuntu, but I wanted to try out the madwifi drivers.  The madwifi drivers were buggy on my system, so now I'm trying to revert back to the original ath5k (or ath9k.. not sure).

At this point I have no wireless capabilities anymore..  Ideas?

---

