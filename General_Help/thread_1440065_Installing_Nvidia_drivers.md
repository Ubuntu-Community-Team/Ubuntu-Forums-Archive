---
title: "Installing Nvidia drivers?"
date: 2010-03-27
forum: General Help
---

### Post by _Sweep_ on 2010-03-27
Hello all, I am a newb and I need help installing Nvidia drivers on my Zotac Ion pc.  I tried downloading the latest drivers but it wouldn't complete the installation.  I did a search and found some information but don't really know what the people were talking about.  If someone could give me a step by step answer of how to do this that would be great.  Keep in mind I have ONLY used windows up to this point.  I'm liking Ubuntu 9.10 so far and hopefully someone will help me out even though this is cake work for most of you.

Thanks!

---

### Post by Sin@Sin-Sacrifice on 2010-03-27
```
apt-cache search nvidia
``` then ```
sudo apt-get install "package from list that you want"
``` Not sure what chip set you have so no way for me to say which to download. More than likely the 185 but you can get the latest from nvidia and run it from CLI.

---

### Post by cryptotheslow on 2010-03-27
What NVidia card is it?

---

### Post by linuxman94 on 2010-03-27
Did you go to System -> Administration -> Hardware Drivers and enable the proprietary driver for your card?

---

### Post by _Sweep_ on 2010-03-27
> **linuxman94 said:**
> Did you go to System -> Administration -> Hardware Drivers and enable the proprietary driver for your card?

Yeah I tried it twice yesterday and it didn't work.  I tried it just now and it worked and the driver installed so I guess I just needed to reboot my system.  Thanks for the replies and the help! ;)

---

