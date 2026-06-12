---
title: "Blacklist kernel module"
date: 2009-09-23
forum: General Help
---

### Post by AMuze on 2009-09-23
Hello,

I am trying to prevent the default ethernet kernel module from being loaded at boot time. I have added it to the /etc//modprobe.d/blacklist.conf file, but it continues to load every boot. I have built the correct module for my eth0 interface and added it to my /etc/modules file. This seems to allow the new module to load at boot. I just can't seem to get the default one to not load. So I can't use the new one without rmmod the old one first.

I understand that i can let it load, ten unload it and load the correct one, but I am looking for the proper method to do this as I may want to use it again in the future.

My question is what am I doing wrong with the blacklist? I've read about some alias expansion, do I need to do something in another file to stop the default module from being loaded? Is it even possible to have the kernel not load the modules it was built with?

I'm running 9.04 on a msi U123 wind. so far it's running pretty nice.

many thanks,
--amuze

---

### Post by Ayuthia on 2009-09-23
It could be that the module is being loaded in the initramfs (what the system uses while it is starting up) and its blacklist file is not updated.  You can try the following:
```
sudo update-initramfs -a
```

Hope that helps.

---

### Post by AMuze on 2009-09-23
awesome, that worked perfectly. many thanks for you help. I was struggling on how to get that default kernel module not to load. everything seems to be working correctly now. my next step is to prune the modules I don't need, and to figure out why my N based 802.11 only connects at ~1Mbps. but that's another post...

many thanks,
--A

---

