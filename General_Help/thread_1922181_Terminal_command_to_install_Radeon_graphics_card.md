---
title: "Terminal command to install Radeon graphics card"
date: 2012-02-08
forum: General Help
---

### Post by Hunt3rr on 2012-02-08
Hello, I'm learning Ubuntu,

but what is the command to install Radeon HD 6570 drivers?  

I have the drivers downloaded, or I could also do it the package way, either way.


Thanks

---

### Post by Rafterman414 on 2012-02-08
Try this:
```
sudo apt-get install fglrx fglrx-amdcccle
```I believe that will download and install the proprietary AMD Radeon Drivers and the Catalyst Control Center. I prefer to go through the repository for the package because every time I have tried to compile and install the drivers from source I managed to break something.

---

### Post by Hunt3rr on 2012-02-08
I have tried several ways to install.  I will try that command as soon as I get home.

---

### Post by Mark Phelps on 2012-02-08
Unless you really need 3D hardware acceleration (for Gaming) or you simply are unable to see a desktop, you do not NEED the restricted Radeon drivers.  If you're seeing a desktop, you already have Radeon drivers installed -- the default open-source drivers.

---

### Post by Hunt3rr on 2012-02-08
```
hunter@Hunter-PC:~$ sudo apt-get install fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
fglrx set to manually installed.
fglrx-amdcccle is already the newest version.
fglrx-amdcccle set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

That comes up when I do that.

---

### Post by Mark Phelps on 2012-02-09
Looks like you already have the restricted drivers installed ...

To confirm, open a terminal and enter "fglrxinfo" ... that will provide some version information.

---

### Post by raja.genupula on 2012-02-09
And along with that provide us  **lspci ** output also.

---

