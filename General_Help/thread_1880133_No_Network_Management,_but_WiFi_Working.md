---
title: "No Network Management, but WiFi Working"
date: 2011-11-13
forum: General Help
---

### Post by steevven1 on 2011-11-13
I just installed Xubuntu 11.10 on an old machine using a PCMCIA wifi card. Everything is working beautifully, but there is one problem:

I installed using the "Alternate CD," and during installation, it asked me to manually type the SSID and passphrase for a nearby wifi network (so it could use the Internet during installation). I did, and it worked perfectly.

Now, when I'm booted into Xubuntu, I have an Internet connection (via wifi...the network I set up during installation), but the network manager icon says "device not managed," and it is impossible for me to choose other wifi networks, disconnect from this one, etc.

How can I get network manager to work properly? My wifi card is clearly functioning just fine.

Thanks in advance!!!

---

### Post by raja.genupula on 2011-11-13
> **steevven1 said:**
> I just installed Xubuntu 11.10 on an old machine using a PCMCIA wifi card. Everything is working beautifully, but there is one problem:

I installed using the "Alternate CD," and during installation, it asked me to manually type the SSID and passphrase for a nearby wifi network (so it could use the Internet during installation). I did, and it worked perfectly.

Now, when I'm booted into Xubuntu, I have an Internet connection (via wifi...the network I set up during installation), but the network manager icon says "device not managed," and it is impossible for me to choose other wifi networks, disconnect from this one, etc.

How can I get network manager to work properly? My wifi card is clearly functioning just fine.

Thanks in advance!!!

sometimes updates are going to give solution to issues like this.

otherwise give a try with re installing your network manager from synaptic.

---

### Post by Jacobonbuntu on 2011-11-13
> **steevven1 said:**
> I just installed Xubuntu 11.10 on an old machine using a PCMCIA wifi card. Everything is working beautifully, but there is one problem:

I installed using the "Alternate CD," and during installation, it asked me to manually type the SSID and passphrase for a nearby wifi network (so it could use the Internet during installation). I did, and it worked perfectly.

Now, when I'm booted into Xubuntu, I have an Internet connection (via wifi...the network I set up during installation), but the network manager icon says "device not managed," and it is impossible for me to choose other wifi networks, disconnect from this one, etc.

How can I get network manager to work properly? My wifi card is clearly functioning just fine.

Thanks in advance!!!

there is a mistake in the installer of Xubuntu 11.10, a part of gigolo network software is missing, some back -end stuff, I will look it up, will be back in a minute...

---

### Post by Jacobonbuntu on 2011-11-13
..............found it, look here
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/878682](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/878682)

as it sais, the gvfs-backends package is missing, I hope this will solve your problem. It did in my case with my netbook...

---

