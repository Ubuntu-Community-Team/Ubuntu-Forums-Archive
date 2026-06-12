---
title: "I uninstalled apt!"
date: 2012-07-30
forum: General Help
---

### Post by lloydwood on 2012-07-30
Hello,

I'm an idiot. I was trying to get some USB perl scripts working and I managed to uninstall apt-get. I was trying to re-install the libusb libraries but in my haste to do so did not notice apt was marked to go with them. Basically I uninstalled libusb-0.1-4. It seems a lot of important stuff gets uninstalled with it!

Is there any way to get it back? The system is my media server so I can't really afford to reinstall the whole thing. There's too much data on there to be moved elsewhere.

The system is working but obviously crippled without these important packages.

Any help would be very gratefully received.

---

### Post by NikTh on 2012-07-30
Hi ,
you can simply download the .deb package (the correct deb package) and install it with
```
sudo dpkg -i <package name>.deb
```Thanks

---

### Post by lloydwood on 2012-07-30
Phew. I'm glad there's a solution.

I'm running Ubuntu Server 12.04 LTS. dpkg -l shows me i need:

apt   0.8.16~exp12ubuntu10.2

I'm not sure where to get if from though.

---

### Post by spjackson on 2012-07-30
> **lloydwood said:**
> Phew. I'm glad there's a solution.

I'm running Ubuntu Server 12.04 LTS. dpkg -l shows me i need:

apt   0.8.16~exp12ubuntu10.2

I'm not sure where to get if from though.
[Here.]("http://packages.ubuntu.com/precise/apt")

---

### Post by lloydwood on 2012-07-30
Thank you very much. Managed to re-install it. Won't be doing that again.

---

### Post by NikTh on 2012-07-30
> **lloydwood said:**
> Managed to re-install it. Won't be doing that again.

Hi ,

glad you solved it. 

Please mark this **thread as solved** from **Thread tools**.

Thanks

---

