---
title: "Virtualbox question?"
date: 2011-09-17
forum: General Help
---

### Post by cowboy7305 on 2011-09-17
Running ubuntu 10.04 have installed virtual-box from synaptic and also the guests add ons i think from memory  its 3.1
every thing went ok not trouble windows xp is running fine mouse is working as it should so is Internet connection 
questions No usb drivers no CD/DVD showing up when i go to computer in xp 
 does usb work on Synaptic version or not
i

---

### Post by haqking on 2011-09-17
> **cowboy7305 said:**
> Running ubuntu 10.04 have installed virtual-box from synaptic and also the guests add ons i think from memory  its 3.1
every thing went ok not trouble windows xp is running fine mouse is working as it should so is Internet connection 
questions No usb drivers no CD/DVD showing up when i go to computer in xp 
 does usb work on Synaptic version or not
i


add the vbox extnesions pack from same download page also. [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and choose the extensions pack

and make sure you are a member of the vboxusers group on your host machine.
```

sudo usermod -a -G vboxusers username 

```

---

### Post by cowboy7305 on 2011-09-17
been there and all i can find is downloads for 4.1 and i have 3.1 and it tells me to only download extension packs for my virtualbox

---

### Post by haqking on 2011-09-17
> **cowboy7305 said:**
> been there and all i can find is downloads for 4.1 and i have 3.1 and it tells me to only download extension packs for my virtualbox


oh yeah your running the old virtual box.

Download the latest from the downloads page or add the ppa and it will update.

3.1 is ancient now ;-)

You will probably need to remove using synaptic and upgrade to latest either using the downloaded .deb or through the ppa.

---

