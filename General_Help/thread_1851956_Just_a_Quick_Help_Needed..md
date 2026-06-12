---
title: "Just a Quick Help Needed."
date: 2011-09-29
forum: General Help
---

### Post by volaer on 2011-09-29
Hello Guys!!! Do you know how can I upgrade to the latest version of Ubuntu without uninstalling my current ubuntu?

I want to upgrade to Ubuntu 11.04 while right now I am using Ubuntu 10.04

---

### Post by mike555 on 2011-09-29
You should keep what you have (for stability) ,you could use gparted from a live cd to partition your hard drive ,so you have a separate area to experiment with ......... or install to a usb drive.

---

### Post by volaer on 2011-09-29
> **mike555 said:**
> You should keep what you have (for stability) ,you could use gparted from a live cd to partition your hard drive ,so you have a separate area to experiment with ......... or install to a usb drive.

Oh... thanks.. so does it mean that 11.04 is not yet stable?

---

### Post by mike555 on 2011-09-29
11.04 may be stable for most people, but why take a chance when 10.04 is supported longer and is working for you ......... it's your call, but I recommend partitioning and that way you can have both...
   if you need help with that let us know, sending us a picture of gparted will help ...

---

### Post by dino99 on 2011-09-29
natty is stable now of course :)

but you cant directly jump to natty from lucid: you need to upgrade to maverick first, then to natty

sudo gedit /etc/apt/sources.list
- change lucid by maverick
- comment all the third party repo (ppa) if any
- save & exit

sudo apt-get update
sudo apt-get upgrade
sudo reboot

and again the same steps to upgrade to natty from maverick

---

### Post by volaer on 2011-09-29
> **mike555 said:**
> 11.04 may be stable for most people, but why take a chance when 10.04 is supported longer and is working for you ......... it's your call, but I recommend partitioning and that way you can have both...
   if you need help with that let us know, sending us a picture of gparted will help ...

Thanks a lot man!!! I just thought it's good to have a nice you look and feel. :)

---

### Post by volaer on 2011-09-29
> **dino99 said:**
> natty is stable now of course :)

but you cant directly jump to natty from lucid: you need to upgrade to maverick first, then to natty

sudo gedit /etc/apt/sources.list
- change lucid by maverick
- comment all the third party repo (ppa) if any
- save & exit

sudo apt-get update
sudo apt-get upgrade
sudo reboot

and again the same steps to upgrade to natty from maverick

Thanks Natty!!! So that's mean two upgrades which take hours and hours... shew... Maybe I will just download the latest version and install it.

---

### Post by mikewhatever on 2011-09-29
Please try a more descriptive thread title in the future.
This is a Help&Support forum, so pretty much everyone needs help, and preferably quick.

---

