---
title: "3d acceleration with 560ti"
date: 2012-03-26
forum: General Help
---

### Post by david99world on 2012-03-26
Hi,

I've recently installed ubuntu and I have a asus560ti.

If I go to system info -> graphics, I have 

Driver - unknown
Experience - standard

How do I enable 3d acceleration so I can use things like compiz etc?

If I try to install cinnamon I get  


You are about to add the following PPA to your system:
 Cinnamon Desktop
 Currently moving and I don't have a computer with Linux 3d acceleration drivers to update the repo.

Also - is it possible to use both cinnamon and the cube together?

Thanks,

---

### Post by dcstar on 2012-03-27
> **david99world said:**
> Hi,

I've recently installed ubuntu and I have a asus560ti.

If I go to system info -> graphics, I have 

Driver - unknown
Experience - standard

How do I enable 3d acceleration so I can use things like compiz etc?

........

That card is supposed to have a Nvidia chipset. Use the Hardware Drivers function to install them.

---

### Post by david99world on 2012-03-27
> **dcstar said:**
> That card is supposed to have a Nvidia chipset. Use the Hardware Drivers function to install them.

Ah, I have done but I still get...

"Driver unknown" "Experience standard"

Should I still get this even if the driver is installed correctly?

---

### Post by Mark Phelps on 2012-03-27
Unfortunately, System Info is unreliable.  I gave Radeon drivers installed in my desktop and it still says "unknown".

If there are Nvidia drivers available for that card, you should be offered something in Additional Drivers.

---

### Post by david99world on 2012-03-28
I guess what makes me slightly more concerned is when I try to install cinnamon I get...does this still mean the drivers aren't installed correctly?  In the additional drivers window I do get a green ticket against nvidia etc.

david@david-P5Q:~$ sudo add-apt-repository ppa:merlwiz79/cinnamon-ppa[sudo] password for david: 
You are about to add the following PPA to your system:
 Cinnamon Desktop
 Currently moving and I don't have a computer with Linux 3d acceleration drivers to update the repo.

Unofficial Cinnamon Desktop PPA
Cinnamon is a Gnome Shell fork.
This ppa will contain the Stable Cinnamon Packages as well as extensions for Cinnamon.

Homepage : [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)

Add Repo:
sudo add-apt-repository ppa:merlwiz79/cinnamon-ppa
sudo apt-get update

Install:
sudo apt-get install cinnamon
Logout and Change the session to Cinnamon.

Weather extension:
Locate your WOEID from here [http://edg3.co.uk/snippets/weather-location-codes/](http://edg3.co.uk/snippets/weather-location-codes/)
 More info: [https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa](https://launchpad.net/~merlwiz79/+archive/cinnamon-ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

---

