---
title: "admin and root are the same thing?"
date: 2010-06-07
forum: General Help
---

### Post by tuxtix on 2010-06-07
I changed my user account from custom to admin already,a problem occured while I run the NVIDIA installer (*.run) by double clicking on it then it said "ERROR: nvidia-installer must be run as root"

How to run this installer file as root?

(please give me the full command text:))

---

### Post by Smart Viking on 2010-06-07
Run

gksudo nautilus

Then you locate what you want to install and double click it, remember to close it. :)

---

### Post by Breambutt on 2010-06-07
I think you need to exit X before you can run those NVIDIA installers and use *sudo* in front of standard commands for temporary root access.

I'd also like to point out that if you're only looking for display drivers, you should probably use the ones in System > Admin > Hardware Drivers with your limited experience, otherwise you might end up with a computer without a graphical interface if you don't know how to fix the mess.

---

### Post by ThesaurusRex on 2010-06-07
> (please give me the full command text)

```
cd (dir)
sudo *.run
```

Where (dir) is the path where your installer exists, and *.run is the name of the installer.

---

### Post by ThesaurusRex on 2010-06-07
> **Breambutt said:**
> I'd also like to point out that if you're only looking for display drivers, you should probably use the ones in System > Admin > Hardware Drivers with your limited experience, otherwise you might end up with a computer without a graphical interface if you don't know how to fix the mess.

He's right, you know.

---

### Post by an0dos on 2010-06-07
> **tuxtix said:**
> I changed my user account from custom to admin already,a problem occured while I run the NVIDIA installer (*.run) by double clicking on it then it said "ERROR: nvidia-installer must be run as root"

How to run this installer file as root?

(please give me the full command text:))

If you're trying to install the nvidia driver, it may be a better idea to install it through the following steps

click on system-->administration-->hardware drivers

---

