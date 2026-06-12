---
title: "iTunes from external hard drive?"
date: 2011-06-07
forum: General Help
---

### Post by Badger864 on 2011-06-07
Hi!

I have old hard drive in an external case. It was dual-boot Vista and Ubuntu 9.04. 

Is there some way to access the Vista OS and run iTunes by using it as an external drive, on my current laptop (which is upgraded to 10.04)

---

### Post by linuxinstalledfromhdd on 2011-06-07
What you would need to do is migrate your data from the Vista to the Linux system manually. Just use your ipod and this in Ubuntu:

[http://www.gtkpod.org/wiki/Home](http://www.gtkpod.org/wiki/Home)

---

### Post by Badger864 on 2011-06-07
I probably wasn't clear in my description.

What I want to do is use the external drive as an interface to iTunes, rather than installing a windows simulator through WINE, or whatever, so I can use that to maintain my iPhone and access other stuff iTunes has.

---

### Post by blueridgedog on 2011-06-07
Do you want to boot from the Vista install on the drive?  What happens when you tell your laptop to boot from the drive?

---

### Post by linuxinstalledfromhdd on 2011-06-07
You can install iTunes in Wine on Ubuntu, but applications running in Wine can't access external devices like USB external drives.  At least that was the impression I always had.

---

### Post by Badger864 on 2011-06-08
Well, rather than booting from the external drive, I was interested if there were a way to run Vista in parallel, on the machine, perhaps in a separate window, by booting from the drive after I had Ubuntu up and running.

---

### Post by blueridgedog on 2011-06-08
Possible, but complex.  See if this points you in a direction:

[http://forums.virtualbox.org/viewtopic.php?f=6&t=3774](http://forums.virtualbox.org/viewtopic.php?f=6&t=3774)

---

### Post by linuxinstalledfromhdd on 2011-06-08
Install Virtualbox 4, in terminal:

```

sudo echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-4.0

```Install Windows Vista in Virtualbox 4. Install the Guest Packages to enable your USB port. Migrate your data from the USB external device to your emulated Vista.

---

### Post by Badger864 on 2011-06-08
Thanks! That's what I was looking for. Will try this evening.

---

