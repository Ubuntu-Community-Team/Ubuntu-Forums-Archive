---
title: "can I save what apt-get downloads from the repos?"
date: 2010-03-20
forum: General Help
---

### Post by garyed on 2010-03-20
I have a laptop with a wireless that needs a driver from what I've read;
```
apt-get install b43-fwcutter 
```
I should be able to plug it in (ethernet) & get it to work but it occurred to me that what if the ethernet didn't work either.
So my question is how could I get the files that command would download to my desktop onto a disk so i could manually install it onto the laptop?

---

### Post by Revolutionary101 on 2010-03-20
Install APTonCD by typing this into terminal.

```
sudo apt-get install aptoncd
```

This will let you save your downloads from apt-get on a CD.

---

### Post by jsriz on 2010-03-20
> **garyed said:**
> I have a laptop with a wireless that needs a driver from what I've read;
```
apt-get install b43-fwcutter 
```I should be able to plug it in (ethernet) & get it to work but it occurred to me that what if the ethernet didn't work either.
So my question is how could I get the files that command would download to my desktop onto a disk so i could manually install it onto the laptop?
I just hope that you are asking how to install this b43-fwcutter offline
use the synaptic manager to "generate package download script"(system->administration->synaptic P.M.->select files to install->file ->generate package download script)
run the script on your desktop
on your laptop press alt+F2 run gksudo nautilus 
copy the files it downloads /var/cache/apt/archives/
and run the command again.

---

### Post by 2hot6ft2 on 2010-03-20
> **jsriz said:**
> I just hope that you are asking how to install this b43-fwcutter offline
use the synaptic manager to "generate package download script"(system->administration->synaptic P.M.->select files to install->file ->generate package download script)
run the script on your desktop
on your laptop press alt+F2 run gksudo nautilus 
copy the files it downloads /var/cache/apt/archives/
and run the command again.
Basically the same but I would suggest saving the script to a usb drive and double clicking on it there so it will download the files to the usb drive where the script is. Choose Run in Terminal so you can see when it finishes.

Reason being if you download a lot of packages you wouldn't want them to fill your desktop and then have to move them. Also using nautilus as root to move them may change the permissions and shouldn't even be necessary.

On the other pc open Synaptic and click on File > Add downloaded packages
That way they get installed in the order they need to be (dependencies first).

---

### Post by garyed on 2010-03-20
Thanks to all for the help.

---

### Post by garyed on 2010-03-20
Well I still can't get my wireless to work but I did get the package downloaded & transferred & it installed but then told me I already had that package in 9.04. Anyways what I did was:
```
sudo apt-get -d install b43-fwcutter
```
It lists the deb file it downloads & doesn't install it so i could just copy it onto usb & run the deb file on my laptop.
I'll mark this thread solved & start another one to see if anyone can help get my wireless working.
Thanks again.

---

