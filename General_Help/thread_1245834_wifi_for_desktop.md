---
title: "wifi for desktop"
date: 2009-08-21
forum: General Help
---

### Post by geogur on 2009-08-21
i need help i tried to set up my wifi , lost my lan line , by enabling back ports and installing wicd bad idea . now what i need to get my wireless working.

---

### Post by geogur on 2009-08-21
i guess what i am pleeing for is for the developers to include wifi detection / conection scripts in the update manager this would be really help full .

---

### Post by wcutrombonekid on 2009-08-21
i've never had a problem connecting to wifi with ubuntu.  its always just automatically picked the network and ran with it, or i would pick it and it ran from there.  it acually connected to networks a lot faster than vista did on this computer.  and its a lot less picky for me

---

### Post by geogur on 2009-08-21
my eeepc detects many networks but  ubuntu dose not detect any networks , this means its a hardware problem i am using a brand new Linksys wireless-g pci adapter but i cant get a conection ?

---

### Post by DonnieP on 2009-08-22
> **geogur said:**
> i need help i tried to set up my wifi , lost my lan line , by enabling back ports and installing wicd bad idea . now what i need to get my wireless working.

Have you uninstalled wicd and re-installed NetworkManager?

---

### Post by matthewbpt on 2009-08-22
You aren't being very helpful, if you want us to help you fix your wifi you could start by telling us what card you have. Is it a usb card or a pci card? If its a usb card, go to the command line and type 'lsusb' and post the output here, if its a pci card then type 'lspci' and post the output here. Also post the output of 'ifconfig' , 'iwconfig' and 'sudo lshw -C Network'

---

### Post by jtravnick on 2009-08-22
> **matthewbpt said:**
> You aren't being very helpful, if you want us to help you fix your wifi you could start by telling us what card you have. Is it a usb card or a pci card? 

He said in his second replay that he has a **linksys pci G** card I am assuming it will be model WMP54G this is the same card I have and out of the box it worked perfict for me with a new install of 9.04 after and update now its hit or miss as to when it will work. I am going to guess that he is having the same problem that I am having as it will see his router and any other routers in range but will not conect to the internet hopefully if I am wrong about his problem he will replay back shortly.

---

