---
title: "Add/Remove Programs does not appear in Administration"
date: 2010-12-24
forum: General Help
---

### Post by virtdave@mcn.org on 2010-12-24
Is there something I must do to make "Add/Remove Programs" to appear in the System>Administration menu in Ubuntu 10.10?

---

### Post by wilee-nilee on 2010-12-24
> **virtdave@mcn.org said:**
> Is there something I must do to make "Add/Remove Programs" to appear in the System>Administration menu in Ubuntu 10.10?


It's called synaptic, or you can use the soft ware center, or a terminal.

---

### Post by spiky001 on 2010-12-24
Open administration/synaptic package manager  then select installed software

---

### Post by sisco311 on 2010-12-24
gnome-app-install (a.k.a. Add/Remove Programs) has been replaced by Ubuntu Software Center.

---

### Post by virtdave@mcn.org on 2010-12-24
Thanks for the responses--I suspected that Add/Remove Programs had been superseded, this confirms it.  However, neither the Software Center, which seems to only install programs from a (very large) list, nor the Synaptic Package Manager seem to be able to recognize a driver package I downloaded, and copied to the Desktop, which is supposed to be valid for Ubuntu -- in fact, it's called UnifiedLinuxDriver_0.86.tar.gz (for a Samsung printer)--I even tried burning a CD with it, and loading from the CD, no luck.

---

### Post by Syed75 on 2010-12-24
```
gksudo synaptic &
```

Run this in the terminal.

---

### Post by sisco311 on 2010-12-25
> **virtdave@mcn.org said:**
> Thanks for the responses--I suspected that Add/Remove Programs had been superseded, this confirms it.  However, neither the Software Center, which seems to only install programs from a (very large) list, nor the Synaptic Package Manager seem to be able to recognize a driver package I downloaded, and copied to the Desktop, which is supposed to be valid for Ubuntu -- in fact, it's called UnifiedLinuxDriver_0.86.tar.gz (for a Samsung printer)--I even tried burning a CD with it, and loading from the CD, no luck.

They don't provide a .deb package, so you can't use the package managers to install the driver. 

You have to download the latest driver from [http://www.samsung.com/us/support/](http://www.samsung.com/us/support/) extract the archive (.tar.gz file) and run cdroot/autorun as root. 

Open a terminal (Applications -> Accessories -> Terminal) and download the driver:
```
cd ~/Desktop
wget http://downloadcenter.samsung.com/content/DR/200911/20091117165757640/UnifiedLinuxDriver_1.00.tar.gz
```

Extract it:
```
tar xfvz UnifiedLinuxDriver_1.00.tar.gz
```

Make sure you have its dependencies installed:
```
sudo apt-get update
sudo apt-get install ghostscript cups sane
```

Start the installer:
```
gksu ./cdroot/autorun
```

Follow the instruction...

---

### Post by virtdave@mcn.org on 2010-12-25
Cisco, I am so impressed.  Very clear guide, which (FINALLY, after days of irritation) got my printer up and running.  It's a great mystery to me how you ferreted out the precise commands necessary.

---

